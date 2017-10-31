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
  .el-rate{
    margin-top: 10px;
  }
</style>
