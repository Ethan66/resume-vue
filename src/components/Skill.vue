<template>
  <div class="skill">
    <div class="content tip">
      <p class="top">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-skill"></use>
        </svg>
      </p>
      <p class="text">主要填写掌握技能名，领域以及自我评分，5星精通，1星了解</p>
    </div>
    <div class="content" v-for="(skill,index) in skills">
      <h2>技能
        <i class="el-icon-remove" v-on:click='removeSkill(index)'></i>
        <i class="el-icon-circle-plus" v-on:click="addSkill"></i>
      </h2>
      <div class="itemEditor">
        <el-form>
          <el-form-item label="技能名称">
            <el-input v-model='skill.name'></el-input>
          </el-form-item>
          <el-form-item label="擅长领域">
            <el-input v-model='skill.scope'></el-input>
          </el-form-item>
          <el-form-item label="自我评分">
            <el-rate v-model="skill.grade"></el-rate>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>

<script>
  export default{
      props:['skills'],
      methods:{
        removeSkill(index){
            return this.skills.splice(index,1)
        },
        addSkill(){
            this.skills.push({name:'',scope:'',grade:''})
        }
      }
  }
</script>

<style lang="scss">
  $color:#409EFF;
  .content{
    border-radius: 6px; overflow: hidden; background: #fff; font-size: 16px;
    box-shadow: 0 2px 10px rgba(0,0,0,.2); margin-bottom: 20px; padding: 10px;
    h2{
      font-weight: normal; margin-bottom: 10px;
    }
    .p_info{
      display: flex; justify-content: space-between; align-items: center;
      .write{
        flex: 1;
        .el-form-item{
          width: 49%; padding-right: 6%; display: inline-block;
        }
        .el-input__inner{
          border: 1px solid #bfcbd9;
        }
      }
      .el-upload{
        float: right; margin-right: 10px;
      }
    }
    .avatar-uploader .el-upload {
      border: 1px dashed #bfcbd9;
      border-radius: 6px;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    .el-textarea__inner{
      border: 1px solid #bfcbd9;
    }
    .avatar-uploader .el-upload:hover {
      border-color: #409EFF;
    }
    .avatar-uploader-icon {
      font-size: 28px;
      color: #8c939d;
      width: 178px;
      height: 178px;
      line-height: 178px;
      text-align: center;
    }
    .avatar {
      width: 178px;
      height: 178px;
      display: block;
    }
  }
  .tip{
    padding: 0;
    p{
      padding: 8px 20px;
      &.text{
        padding: 15px 20px; color: #666;
      }
    }
    .icon{
      width: 22px; height: 22px;
    }
    .top{
      background: $color; color: #fff;
    }
  }
  .itemEditor {
    .el-form-item {
      width: 49%; display: inline-block; padding-right: 3%;
    }
    .el-form-item:nth-child(2n) {
      padding-right: 0; padding-left: 3%; float: right;
    }
    .el-date-editor {
      width: 100%;
    }
    .el-input__inner {
      border: 1px solid #bfcbd9;
    }
    .width100 {
      width: 100%; padding-right: 0;
    }
  }

  .el-rate{
    margin-top: 10px;
  }
</style>
