<template>
  <div id="top">
    <div class="log">
    </div>
    <div class="actions">
      <el-button type="primary" @click="signUp = true">
        <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-zhuce"></use>
      </svg>注册</el-button>
      <el-button @click="login = true">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-denglu"></use>
        </svg>登录</el-button>
    </div>
    <el-dialog title="注册" :visible.sync="signUp" width="50%" :before-close="handleClose">
      <span>这是一段信息</span>
      <span slot="footer" class="dialog-footer">
      <el-button @click="signUp = false">取 消</el-button>
      <el-button type="primary" @click="signUp = false">确 定</el-button>
    </span>
    </el-dialog>
    <el-dialog title="登陆" :visible.sync="login" width="50%" :before-close="handleClose">
      <span>这是一段信息</span>
      <span slot="footer" class="dialog-footer">
      <el-button @click="login = false">取 消</el-button>
      <el-button type="primary" @click="login = false">确 定</el-button>
    </span>
    </el-dialog>
    <!--<div class="signUp">
      <el-form :model="ruleForm2" status-icon :rules="rules2" ref="ruleForm2" label-width="100px" class="demo-ruleForm">
        <el-form-item label="密码" prop="pass">
          <el-input type="password" v-model="ruleForm2.pass" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="确认密码" prop="checkPass">
          <el-input type="password" v-model="ruleForm2.checkPass" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="年龄" prop="age">
          <el-input v-model.number="ruleForm2.age"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm2')">提交</el-button>
          <el-button @click="resetForm('ruleForm2')">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div class="login"></div>-->
  </div>
</template>

<script>
  export default{
      data(){
          return {
            signUp: false,login:false
          }
      },
    methods:{
      handleClose(done) {
        this.$confirm('确认关闭？')
          .then(_ => {
            done();
          })
          .catch(_ => {});
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
  }

</style>
