<template>
  <div class="profile">
    <div class="content tip">
      <p class="top">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-ren"></use>
        </svg>
      </p>
      <p class="text">主要填写名字，专业以及联系方式</p>
    </div>
    <div class="content">
      <h2>个人信息</h2>
      <el-form class="p_info">
        <div class="write">
          <el-form-item label="姓名">
            <el-input placeholder="请输入姓名" v-model='profile.name'></el-input>
          </el-form-item>
          <el-form-item label="职位意向">
            <el-input placeholder="请输入职位" v-model='profile.workDirection'></el-input>
          </el-form-item>
          <el-form-item label="邮箱">
            <el-input placeholder="请输入有效邮箱" v-model='profile.email'></el-input>
          </el-form-item>
          <el-form-item label="电话">
            <el-input placeholder="请输入手机号码" v-model='profile.number'></el-input>
          </el-form-item>
          <el-form-item label="年龄">
            <el-input placeholder="请输入内容" v-model='profile.age'></el-input>
          </el-form-item>
          <el-form-item label="社交网站">
            <el-input placeholder="请输入网站名称" v-model='profile.website'></el-input>
          </el-form-item>
        </div>
        <div class="portrait">
          <el-upload
            class="avatar-uploader"
            action="https://jsonplaceholder.typicode.com/posts/"
            :show-file-list="false"
            :on-success="handleAvatarSuccess"
            :before-upload="beforeAvatarUpload">
            <img v-if="profile.imageUrl" :src="profile.imageUrl" class="avatar">
            <i v-else class="el-icon-plus avatar-uploader-icon"></i>
          </el-upload>
        </div>
      </el-form>
    </div>
    <div class="content">
      <h2>地址 </h2>
      <el-input
        type="textarea"
        :rows="1"
        placeholder="请输入内容" v-model="profile.address"
      >
      </el-input>
    </div>
    <div class="content">
      <h2>个人评价</h2>
      <el-input
        type="textarea"
        :rows="3"
        placeholder="请输入内容" v-model="profile.summary"
      >
      </el-input>
    </div>
  </div>
</template>

<script>
  export default{
      props:['profile'],
    components:{

    },
      data(){
          return {

          }
      },
    methods:{
      handleAvatarSuccess(res, file) {
        this.imageUrl = URL.createObjectURL(file.raw);
      },
      beforeAvatarUpload(file) {
        const isJPG = file.type === 'image/jpeg';
        const isLt2M = file.size / 1024 / 1024 < 2;

        if (!isJPG) {
          this.$message.error('上传头像图片只能是 JPG 格式!');
        }
        if (!isLt2M) {
          this.$message.error('上传头像图片大小不能超过 2MB!');
        }
        return isJPG && isLt2M;
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
</style>
