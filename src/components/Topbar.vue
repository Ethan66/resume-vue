<template>
  <div id="top">
    <div class="log">
    </div>
    <div class="actions" v-if='actionType.signOrLogin'>
      <el-button type="primary" @click="actionType.signUp = true">
        <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-zhuce"></use>
      </svg>注册</el-button>
      <el-button @click="actionType.login = true">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-denglu"></use>
        </svg>登录</el-button>
    </div>
    <div class="logining" v-if='!actionType.signOrLogin'>
      用户：<span style="margin-right: 10px;">{{currentUser.username}}</span>
      <el-button type="primary" v-on:click='saveOrUpdateResumes'>
        <svg class="icon save" aria-hidden="true">
          <use xlink:href="#icon-yun"></use>
        </svg>保存
      </el-button>
      <el-button v-on:click='logout'>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-dengchutuichuguanbi"></use>
        </svg>登出
      </el-button>
    </div>
    <el-dialog title="注册" :visible.sync="actionType.signUp" width="500px">
      <el-form :label-position="labelPosition" label-width="80px">
        <el-form-item label="用户名">
          <el-input v-model="formData.username" ></el-input>
        </el-form-item>
        <el-form-item label="密码">
          <el-input type="password" v-model="formData.password" ></el-input>
        </el-form-item>
        <el-form-item>
          <el-button @click="actionType.signUp = false">取 消</el-button>
          <el-button @click="signUp">确 定</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
    <el-dialog title="登录" :visible.sync="actionType.login" width="50%">
      <el-form :label-position="labelPosition" label-width="80px">
        <el-form-item label="用户名">
          <el-input v-model="formData.username" ></el-input>
        </el-form-item>
        <el-form-item label="密码">
          <el-input type="password" v-model="formData.password" ></el-input>
        </el-form-item>
        <el-form-item>
          <el-button @click="actionType.login = false">取 消</el-button>
          <el-button @click="login">确 定</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
  </div>
</template>

<script>
  import AV from 'leancloud-storage'
  export default{
      props:['resume'],
      //created走在data（）后面，当数据初始化好了以后，created才执行
      //当用户没有请求AV.User.logOut()时，账号不会主动退出，刷新也不会退,但是数据会没有，所以要在created里面先拿一下数据
      created(){
          this.currentUser=this.getCurrent()
        if(this.currentUser.id){
          this.actionType.signOrLogin=false
        }

      },
     /* computed:{
        currentUser:{
            get(){
                return this.getCurrent()
            }
        }
      },*/
      data(){
          return {
            labelPosition: 'right',
              actionType:{signUp:false,login:false,signOrLogin:true},
            formData:{username:'',password:''},
            currentUser:{}
          }
      },
    methods:{
      getCurrent(){
          var current=AV.User.current()
          if(current){
            let {attributes:{username},id}=current
            return {id,username}
          }
          return null
      },
      signUp(){
        let user = new AV.User();
        user.setUsername(this.formData.username);
        user.setPassword(this.formData.password);
        user.signUp().then( (loginedUser)=> {
          this.actionType.signUp=false
          this.actionType.signOrLogin=false
          this.currentUser=this.getCurrent()
         // console.log(this.currentUser)
          this.$message({
            type: 'success',
            message: '注册成功!'
          });
        }, (error)=>{
          this.$message({
            type: 'info',
            message: "注册失败！"
          });
        });
      },
      login(){
        AV.User.logIn(this.formData.username, this.formData.password).then( (loginedUser)=>{
          this.actionType.login=false
          this.actionType.signOrLogin=false
          this.currentUser=this.getCurrent()
          window.location.reload()
         // console.log(this.currentUser)
          this.$message({
            type: 'success',
            message: '登录成功!'
          });
        }, (error)=>{
          this.$message({
            type: 'info',
            message: "登录失败！"
          });
        });
      },
      saveResume(){
        let dataString = JSON.stringify(this.resume)
        var AVresumes = AV.Object.extend('Allresumes');
        var avResumes = new AVresumes();
        var acl = new AV.ACL()
        acl.setReadAccess(AV.User.current(),true)
        acl.setWriteAccess(AV.User.current(),true)
        avResumes.set('content', dataString);
        avResumes.setACL(acl)
        avResumes.save().then((resume)=>{
          this.resume.id = resume.id
          console.log('保存成功');
        }, function (error) {
          alert('保存失败');
        });
      },
      updateResumes(){
        let dataString = JSON.stringify(this.resume)
        let avResumes = AV.Object.createWithoutData('Allresumes', this.resume.id)
        avResumes.set('content', dataString)
        avResumes.save().then(()=>{
          console.log('更新成功')
        })
      },
      saveOrUpdateResumes(){
        if(this.resume.id){
          this.updateResumes()
        }else{
          this.saveResume()
        }
      },
      logout(){
        AV.User.logOut()
        this.currentUser = null
        window.location.reload()
      }
    }
  }
</script>

<style lang="scss">
  #top{
    display: flex; justify-content: space-between; align-items: center;
    padding: 16px;
    font-size: 20px; border-bottom: 1px solid #ddd; box-shadow: 0 0 3px rgba(0,0,0,.3); background: #fff;
    .el-button{
      padding: 8px 16px;
    }
    .actions{
      .icon{
        width: 20px; height: 18px; vertical-align: -3px;
      }
    }
    .logining{
      button{
        padding: 6px 16px;
      }
      .icon{
        width: 20px; height: 22px; vertical-align: -5px;
        &.save{
          width: 26px;
        }
      }
    }
    .el-dialog{
      border-radius: 6px;
    }
    .el-dialog__body{
      padding: 20px 40px 10px 15px;
      .el-form-item:last-child{
        .el-form-item__content{
          text-align: center; margin-left: 0 !important;
        }
        button{
          margin-right: 30px;
        }
        input[type=submit]{
          display: inline-block; line-height: 1; white-space: nowrap; cursor: pointer; background: #fff; border: 1px solid #d8dce5;
          color: #5a5e66; -webkit-appearance: none; text-align: center; box-sizing: border-box; outline: 0;
          margin: 0; -webkit-transition: .1s; transition: .1s; padding: 12px 20px; border-radius: 4px;
          font-size: 14px; padding: 8px 16px; background: #409eff; color: #fff;
        }
      }
    }
  }

</style>
