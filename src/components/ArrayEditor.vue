<template>
  <div class="item">
    <div class="content tip">
      <p class="top">
        <svg class="icon" aria-hidden="true">
          <use v-bind:xlink:href="'#icon-'+icons"></use>
        </svg>
      </p>
      <p class="text">{{textContent}}</p>
    </div>
    <div class="content" v-for="(work,index) in items">
      <!--{{work}}-->
      <h2>{{title.zero}} {{index+1}}
        <i class="el-icon-remove" v-on:click='removeCompany(index)'></i>
        <i class="el-icon-circle-plus" v-on:click="addCompany"></i>
      </h2>
      <div class="itemEditor">
        <el-form>
          <el-form-item v-bind:label="title.one">
            <el-input  v-model='work[keys[0]]'></el-input>
          </el-form-item>
          <el-form-item v-bind:label="title.two">
            <el-input  v-model='work[keys[1]]'></el-input>
          </el-form-item>
          <el-form-item v-bind:label="title.three">
            <el-input  v-model='work[keys[2]]'></el-input>
          </el-form-item>
          <el-form-item v-bind:label="title.four">
            <el-date-picker
              v-model="work[keys[3]]"
              type="daterange"
              range-separator="至"
              start-placeholder="开始日期"
              end-placeholder="结束日期">
            </el-date-picker>
          </el-form-item>
          <el-form-item v-bind:label="title.five" class="width100">
            <el-input
              type="textarea"
              :rows="3"
               v-model="work[keys[4]]"
            >
            </el-input>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>

<script>
  import '../assets/arrayEditor.scss'
  export default{
      props:["items",'title','textContent','icons'],
    computed:{
          keys(){
              return Object.keys(this.items[0]);
          }
    },
      data(){
          return {

          }
      },
    methods:{
      addCompany(){
          const empty={}
          this.keys.map(function(value,index){
              empty[value]=''
          })
        this.items.push(empty)
      },
      removeCompany(index){
        this.items.splice(index,1)
      }
    }
  }
</script>

<style lang="scss">

</style>
