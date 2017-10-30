<template>
  <div id="app">
    <Nav1 class="nav1" v-bind:currentTab="currentTab" />
    <Editor class="editor" v-bind:currentTab="currentTab" />
  </div>
</template>

<script>
  import Nav1 from './components/Nav1'
  import Editor from './components/Editor'

export default {
  name: 'app',
  components: {
    Nav1,Editor
  },
  data(){
      return {
          currentTab:0
      }
  }
}
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    display: flex;
  }
  .icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }
  .nav1{

  }
  .editor{
    flex: 1;
  }

</style>
