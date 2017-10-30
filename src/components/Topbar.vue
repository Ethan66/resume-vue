<template>
  <div id="top">
    <div class="log">
    </div>
    <div class="actions">
      <el-button type="primary"><svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-zhuce"></use>
      </svg>注册</el-button>
      <el-button>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-denglu"></use>
        </svg>登录</el-button>
    </div>
  </div>
</template>

<style lang="scss">
  #top{
    display: flex; justify-content: space-between; align-items: center;
    padding: 16px;
    font-size: 20px; border-bottom: 1px solid #ddd; box-shadow: 0 0 3px rgba(0,0,0,.3);
    .el-button{
      padding: 8px 16px;
    }
    .actions{
      .icon{
        width: 20px; height: 18px; vertical-align: -3px;
      }
    }
  }
</style>
