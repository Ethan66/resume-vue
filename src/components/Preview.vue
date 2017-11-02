<template>
  <div id="preview">
    <!--{{resume}}-->
    <div class="preContent">
      <h1>个人简历</h1>
      <div class="info">
        <div class="text">
          <ul>
            <li>
              <span>姓&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;名</span>Ethan
            </li>
            <li>
              <span>求职意向</span>web前端
            </li>
            <li>
              <span>电&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;话</span>12345678910
            </li>
            <li>
              <span>邮&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;箱</span>1224604327@qq.com
            </li>
          </ul>
          <ul>
            <li>
              <span>身&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;高</span>150
            </li>
            <li>
              <span>年&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;龄</span>24
            </li>
            <li>
              <span>学&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;历</span>本科
            </li>
            <li>
              <span>社交网站</span>百度淘宝
            </li>
          </ul>
        </div>
        <div class="img">
          <p></p>
        </div>
      </div>
      <div class="education">
        <h3>
          <span>教育背景</span>
        </h3>
        <ol>
          <li>
            <p>2000/09-2003/6</p><p>杭州师范大学(本科)</p><p>信息工程</p>
            <div class="text">
              <p>在校荣誉：</p>
              <p>水果的风格的个好地方蝶粉蜂黄发货单给</p>
            </div>
          </li>
        </ol>
      </div>
      <div class="experience">
        <h3>
          <span>工作经历</span>
        </h3>
        <ol>
          <li>
            <p>2000/09-2003/6</p><p>杭州师范大学(本科)</p><p>信息工程</p>
            <div class="text">
              <p>工作内容：</p>
            </div>
          </li>
        </ol>
      </div>
      <div class="project">
        <h3>
          <span>项目经验</span>
        </h3>
        <ol>
          <li>
            <p>2000/09-2003/6</p><p>杭州师范大学(本科)</p><p>信息工程</p>
            <div class="text">
              <p>总结：</p>
            </div>
          </li>
        </ol>
      </div>
      <div class="skill">
        <h3>
          <span>个人技能</span>
        </h3>
        <ol class="text">
          <p>前端：html+css,js,jq 5分</p>
          <p>前端：html+css,js,jq 5分</p>
          <p>前端：html+css,js,jq 5分</p>
        </ol>
      </div>
      <div class="appraise">
        <h3>
          <span>个人评价</span>
        </h3>
        <div class="text">

        </div>
      </div>
    </div>
    <div class="btn">
      <el-button-group>
        <el-button type="primary" icon="el-icon-arrow-left">上一页</el-button>
        <el-button type="primary" v-on:click='show.show=true'><i class="el-icon-share"></i>退出预览</el-button>
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
    width: 100%; min-height: 100vh; background: #ddd; font-family: microsoft yahei;
    .preContent{
      width: 800px; min-height: 100vh; margin: 0 auto; margin-top: 30px; background: #fff; padding: 60px;
      h1{
        background: #ddd; text-align: center; color: #000; font-weight: normal; font-size: 30px; padding: 15px 0;
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
              margin-bottom: 20px;
            }
            span{
              font-weight: bold; margin-right: 20px;
            }
          }
        }
        .img{
          width: 150px; height: 170px; background: #bbb;
        }
      }
      h3{
        background: #ddd; margin: 20px 0;
        span{
          display: inline-block; padding: 8px 20px; background: #666; color: #fff;
        }
      }
      .education,.experience,.project,.appraise{
        li{
          >p{
            display: inline-block; margin-right: 100px;
          }
          .text{
            margin-top: 10px;
            p{
              padding-bottom: 6px;
            }
          }
        }
      }
      .skill{
        .text{
          display: flex; justify-content: space-between;
        }
      }
    }
    .btn{
      position: fixed; bottom: 0; right: 0;
    }
  }
</style>
