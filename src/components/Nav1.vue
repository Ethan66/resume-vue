<template>
  <div id="nav">
    <h1>Resume</h1>
    <dl>
      <dt><span>Fill in your resume</span></dt>
      <dd v-for="i in [0,1,2,3,4]" v-bind:class="{active:currentTab.tab==i}" v-on:click="currentTab.tab=i">
        <svg class="icon" aria-hidden="true">
          <use v-bind:xlink:href="'#icon-'+icons[i]"></use>
        </svg>
        <span>{{tabName[i]}}</span>
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
      props:['currentTab','icons'],
      data(){
          return {
              tabName:['Person Info','Experience','Education','Skills','Projects']
          }
      }
  }
</script>

<style lang="scss">
  $color:#409EFF;
  #nav{
    width: 24em; height: 100vh; background: #2e353e; color: #aaa; position: fixed; top:0; left:0; z-index: 100;
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
