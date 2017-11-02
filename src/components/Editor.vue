<template>
  <div id="editor">
    <Topbar v-bind:resume='resume' />
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
    <div class="btn">
      <el-button-group>
        <el-button type="primary" icon="el-icon-arrow-left">上一页</el-button>
        <el-button type="primary" v-on:click='show.show=true'><i class="el-icon-share"></i>点击预览</el-button>
        <el-button type="primary">下一页<i class="el-icon-arrow-right el-icon--right"></i></el-button>
      </el-button-group>
    </div>
  </div>
</template>

<script>
  import Topbar from './Topbar'
  import Profile from './Profile'
  import ArrayEditor from './ArrayEditor'
  import Skill from './Skill'

  export default{
      props:['currentTab','resume','icons','show'],
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
    }
    .btn{
      position: fixed; bottom: 0; right: 0;
    }
  }
</style>
