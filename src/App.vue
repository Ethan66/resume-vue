<template>
  <div id="app">
    <Nav1 class="nav1" v-bind:currentTab="currentTab" v-bind:icons='icons' />
    <Editor class="editor" v-bind:currentTab="currentTab" v-bind:icons='icons' v-bind:resume="resume" />
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
          currentTab:{
              tab:0
          },
        icons:['user','gongwenbao','xueshimao','skill','xiangmu']
        ,
        resume:{
          profile:{
              name:'',workDirection:'',email:'',number:'',age:'',website:'',imageUrl:'',address:'',summary:''
          },
          company:[
            {name:'',department:'',position:'',date:'',content:''}
          ],
          education:[
            {name:'',degree:'',profession:'',date:'',award:''}
          ],
          skills:[
            {name:'',scope:'',grade:''}
          ],
          projects:[
            {website:'',module:'',position:'',date:'',summary:''}
          ]
        }
      }
  },
  methods:{

  }
}
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    min-height: 100vh;
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
    flex: 1; background: #f2f2f2; margin-left: 24em;
  }

</style>
