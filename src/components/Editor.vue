<template>
  <div id="editor">

  </div>
</template>

<style lang="scss">
  #editor{
    min-height: 100px;
    display: flex;
    nav{
      background: #000; width: 80px;
      >ol{
        li{
          text-align: center; padding: 16px 0;
          .icon{
            width: 32px; height: 32px; fill: white;
          }
          &.active{
            background: white;
            > .icon{
              fill: black;
            }
          }
        }
      }
    }
    .panes{
      flex: 1;
      li{
        display: none; height: 100%; overflow: auto;
        padding: 32px;
        &.active{
          display: block;
        }
        .container{
          position: relative;
          .el-icon-circle-cross{
            position: absolute; right: 0; top: 0;
          }
        }
      }
    }

  }
</style>
