<template>
  <div id="nav">
    <h1>Resume</h1>
    <dl>
      <dt><span>Fill in your resume</span></dt>
      <dd v-bind:class="{active:currentTab==0}" v-on:click="currentTab=0">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-user"></use>
        </svg>
        <span>Person Info</span>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-bianji"></use>
        </svg>
      </dd>
      <dd v-bind:class="{active:currentTab==1}" v-on:click="currentTab=1">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-gongwenbao"></use>
        </svg>
        <span>Experience</span>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-bianji"></use>
        </svg>
      </dd>
      <dd v-bind:class="{active:currentTab==2}" v-on:click="currentTab=2">
        <svg class="icon education" aria-hidden="true">
          <use xlink:href="#icon-xueshimao"></use>
        </svg>
        <span>Education</span>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-bianji"></use>
        </svg>
      </dd>
      <dd>
        <svg class="icon skill" aria-hidden="true">
          <use xlink:href="#icon-skill"></use>
        </svg>
        <span>Skills</span>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-bianji"></use>
        </svg>
      </dd>
      <dd>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-xiangmu"></use>
        </svg>
        <span>Projects</span>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-bianji"></use>
        </svg>
      </dd>
    </dl>
    <dl>
      <dt><span>Preview</span></dt>
      <dd>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-heartbeat"></use>
        </svg>
        <span>Show</span>
      </dd>
    </dl>
  </div>
</template>

<script>
  export default{
      props:['currentTab'],
      data(){
          return {

          }
      }
  }
</script>

<style lang="scss">
  $color:#409EFF;
  #nav{
    width: 24em; background: #2e353e; color: #aaa;
    h1{
      text-align: center; margin-top: 50px; margin-bottom: 50px; letter-spacing: 5px;
    }
    dl{
      margin-bottom: 30px;
      dt{
        padding-left: 30px; border-bottom: 1px solid; position: relative; margin-bottom: 30px;
        span{
          padding: 0 10px; font-size: 14px; text-transform: uppercase; background: #2e353e;  position: absolute; top: -8px;
        }
      }
      dd{
        margin-bottom: 2px; padding: 10px 30px; border-left: 3px solid transparent; transition: all .4s;
        &:hover,&.active{
          border-left-color:$color; background:#3e4650; cursor: pointer;
        }
        .icon{
          width: 24px; height: 24px; fill: #aaa;
          &.education{
            width: 26px;
         }
          &.skill{
            width: 30px;
          }
        }
        & .icon:last-child{
          float: right; width: 22px;
        }
        span{
          padding-left: 20px; vertical-align: 5px;
        }
      }
    }
  }
</style>
