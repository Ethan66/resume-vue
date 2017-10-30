<template>
  <div id="editor">
    <Topbar />
    <ol>
      <li v-show="currentTab.tab==0">
        <el-container>
          <el-header>Header</el-header>
          <el-main>Main</el-main>
        </el-container>
      </li>
      <li v-show="currentTab.tab==1">2</li>
      <li v-show="currentTab.tab==2">3</li>
      <li v-show="currentTab.tab==3">4</li>
      <li v-show="currentTab.tab==4">5</li>
    </ol>
  </div>
</template>

<script>
  import Topbar from './Topbar'

  export default{
      props:['currentTab'],
      components:{
          Topbar
      },
    methods:{

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
    .el-header, .el-footer {
      background-color: $color;
      color: #fff;
      text-align: center;
      line-height: 30px;
    }
    .el-main {
      background-color: #E9EEF3;
      color: #333;
      text-align: center;
      line-height: 160px;
    }
  }
</style>
