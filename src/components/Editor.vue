<template>
  <div id="editor">
    <Topbar />
    <ol>
      <li v-show="currentTab.tab==0">
        <Profile v-bind:profile='resume.profile' />
      </li>
      <li v-show="currentTab.tab==1">
        <ArrayEditor v-bind:items="resume.company" v-bind:title="{zero:'公司',one:'公司名称',two:'所属部门',three:'职位',four:'日期',five:'工作经历'}"
             v-bind:textContent="'主要填写前公司名，所属部门,主要职位以及工作内容'" v-bind:icons="icons[1]" />
      </li>
      <li v-show="currentTab.tab==2">
        <ArrayEditor v-bind:items="resume.education" v-bind:title="{zero:'学校',one:'学校名称',two:'学位',three:'专业',four:'日期',five:'在校荣誉'}"
             v-bind:textContent="'主要填写学校名，所学专业，学位以及在校荣誉'" v-bind:icons="icons[2]" />
      </li>
      <li v-show="currentTab.tab==3">
        <Skill v-bind:skills="resume.skills" />
      </li>
      <li v-show="currentTab.tab==4">
        <ArrayEditor v-bind:items="resume.projects" v-bind:title="{zero:'项目',one:'预览地址',two:'负责版块',three:'团队定位',four:'日期',five:'总结'}"
            v-bind:textContent="'主要填写在线项目预览、负责模块、团队定位、项目时长，以及在本项目里面的收获与体会'" v-bind:icons="icons[4]" />
      </li>
    </ol>
  </div>
</template>

<script>
  import Topbar from './Topbar'
  import Profile from './Profile'
  import ArrayEditor from './ArrayEditor'
  import Skill from './Skill'

  export default{
      props:['currentTab','resume','icons'],
      components:{
          Topbar,Profile,ArrayEditor,Skill
      },
    methods:{
        addCompany(){
            this.resume.company.push({name:'',department:'',position:'',date:'',content:''})
        },
      removeCompany(index){
           this.resume.company.splice(index,1)
      }
    }
  }
</script>

<style lang="scss">
  $color:#409EFF;
  #editor{
    ol{
      padding: 50px;
      li{

      }
    }
    .content{
      border-radius: 6px; overflow: hidden; background: #fff; font-size: 16px;
      box-shadow: 0 2px 10px rgba(0,0,0,.2); margin-bottom: 20px; padding: 10px;
      h2{
        font-weight: normal; margin-bottom: 10px;
        i{
          float: right; margin-right: 10px; font-size: 30px;
        }
        .el-icon-remove{
          color: red;
        }
      }
      /*.p_info{
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
      }*/
      .company{
        .el-form-item{
          width: 49%; display: inline-block; padding-right: 3%;
        }
        .el-form-item:nth-child(2n){
          padding-right: 0; padding-left: 3%; float: right;
        }
        .el-date-editor{
          width: 100%;
        }
        .el-input__inner {
          border: 1px solid #bfcbd9;
        }
        .width100{
          width: 100%; padding-right: 0;
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
  }
</style>
