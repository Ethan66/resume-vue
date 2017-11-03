<template>
  <div id="preview">
    <div class="preContent">
      <h1>个人简历</h1>
      <div class="info">
        <div class="text">
          <ul>
            <li>
              <span>姓&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;名</span>{{resume.profile.name}}
            </li>
            <li>
              <span>求职意向</span>{{resume.profile.workDirection}}
            </li>
            <li>
              <span>电&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;话</span>{{resume.profile.number}}
            </li>
            <li>
              <span>邮&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;箱</span>{{resume.profile.email}}
            </li>
          </ul>
          <ul>
            <li>
              <span>身&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;高</span>{{resume.profile.height}}
            </li>
            <li>
              <span>年&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;龄</span>{{resume.profile.age}}
            </li>
            <li>
              <span>学&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;历</span>{{resume.profile.education}}
            </li>
            <li>
              <span>社交网站</span>{{resume.profile.website}}
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
          <li v-for="(school,index) in resume.education">
            <p>
              {{getYYMMDD(school.date[0])}}
              <span v-if="school.date[0]">-</span>
              {{getYYMMDD(school.date[1])}}
            </p>
            <p>{{school.name}}<span v-if="school.degree">({{school.degree}})</span></p><p>{{school.profession}}</p>
            <div class="text">
              <p v-if="school.award">在校荣誉：</p>
              <p>{{school.award}}</p>
            </div>
          </li>
        </ol>
      </div>
      <div class="experience">
        <h3>
          <span>工作经历</span>
        </h3>
        <ol>
          <li v-for="(company,index) in resume.company">
            <p>{{getYYMMDD(company.date[0])}}
              <span v-if="company.date[0]">-</span>
              {{getYYMMDD(company.date[1])}}</p>
            <p>{{company.name}} <span v-if='company.department'>({{company.department}})</span></p><p>{{company.position}}</p>
            <div class="text">
              <p v-if="company.content">工作内容：</p>
              <p>{{company.content}}</p>
            </div>
          </li>
        </ol>
      </div>
      <div class="project">
        <h3>
          <span>项目经验</span>
        </h3>
        <ol>
          <li v-for="(project,index) in resume.projects">
            <p>{{getYYMMDD(project.date[0])}}
              <span v-if="project.date[0]">-</span>
              {{getYYMMDD(project.date[1])}}
            </p><p>{{project.module}}<span v-if="project.position">({{project.position}})</span></p><p>{{project.website}}</p>
            <div class="text">
              <p v-if="project.summary">总结：</p>
              <p>{{project.summary}}</p>
            </div>
          </li>
        </ol>
      </div>
      <div class="skill">
        <h3>
          <span>个人技能</span>
        </h3>
        <ol class="text">
          <p v-for='(skill,index) in resume.skills'>
            <span v-if="skill.name">{{skill.name}}：</span>{{skill.scope}} <span v-if="skill.grade">{{skill.grade}}分</span>
          </p>
        </ol>
      </div>
      <div class="appraise">
        <h3>
          <span>个人评价</span>
        </h3>
        <div class="text">
          {{resume.profile.summary}}
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
      },
    methods:{
      getYYMMDD(date){
        if(date){
          var date1=new Date(date);
          var year=date1.getFullYear();
          var month=date1.getMonth()+1;
          if(month<10){
              month="0"+month
          }
          var d=date1.getDate();
          return year+'/'+month+'/'+d
        }
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
            &:nth-child(3){
              margin-right: 0;
            }
          }
          .text{
            margin-top: 10px; margin-bottom: 10px;
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
