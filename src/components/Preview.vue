<template>
  <div id="preview">
    <!--{{resume}}-->
    <div class="preContent">
      <h1>个人简历</h1>
      <div class="info">
        <div class="text">
          <ul>
            <li>
              <span>姓 名 </span>Ethan
            </li>
            <li>
              <span>民 族 </span>汉
            </li>
            <li>
              <span>姓 名 </span>Ethan
            </li>
            <li>
              <span>民 族 </span>汉
            </li>
          </ul>
          <ul>
            <li>
              <span>姓 名 </span>Ethan
            </li>
            <li>
              <span>民 族 </span>汉
            </li>
            <li>
              <span>姓 名 </span>Ethan
            </li>
            <li>
              <span>民 族 </span>汉
            </li>
          </ul>
        </div>
        <div class="img">
          <p></p>
        </div>
      </div>
    </div>
    <div class="btn">
      <el-button-group>
        <el-button type="primary" icon="el-icon-arrow-left">上一页</el-button>
        <el-button type="primary" v-on:click='show.show=false'><i class="el-icon-share"></i>退出预览</el-button>
        <el-button type="primary">下一页<i class="el-icon-arrow-right el-icon--right"></i></el-button>
      </el-button-group>
    </div>
  </div>
</template>

<script>
  export default{
      props:['resume','show'],
      data(){
          return {

          }
      }
  }
</script>

<style lang="scss">
  #preview{
    width: 100%; min-height: 100vh; background: #ddd;
    .preContent{
      width: 800px; min-height: 100vh; margin: 0 auto; margin-top: 30px; background: #fff; padding: 60px;
      h1{
        background: #bbb; text-align: center; color: #000; font-weight: normal; font-size: 30px; padding: 15px 0;
      }
      .info{
        display: flex;
        .text{
          display: flex; flex: 1; font-size: 16px; padding: 20px 0 0 10px; margin-right: 30px;
          ul{
            &:first-child{
              flex: 4;
            }
            &:last-child{
              flex: 2;
            }
            li{
              margin-bottom: 10px;
            }
            span{
              font-weight: bold; letter-spacing: 10px;
            }
          }
        }
        .img{
          width: 150px; height: 180px; background: #bbb;
        }
      }
    }
    .btn{
      position: fixed; bottom: 0; right: 0;
    }
  }
</style>
