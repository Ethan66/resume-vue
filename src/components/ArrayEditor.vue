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
  $color:#409EFF;
  .item {
    .content {
      border-radius: 6px; overflow: hidden; background: #fff; font-size: 16px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, .2); margin-bottom: 20px; padding: 10px;
      h2 {
        font-weight: normal; margin-bottom: 10px;
        i {
          float: right; margin-right: 10px; font-size: 30px;
        }
        .el-icon-remove {
          color: red;
        }
      }
    }
    .tip {
      padding: 0;
      p {
        padding: 8px 20px;
        &.text {
          padding: 15px 20px; color: #666;
        }
      }
      .icon {
        width: 22px; height: 22px;
      }
      .top {
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
  }
</style>
