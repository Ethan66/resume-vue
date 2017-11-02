<template>
  <div id="app">
    <Nav1 class="nav1" v-show="preview.show" v-bind:currentTab="currentTab" v-bind:icons='icons' />
    <Editor class="editor" v-show="preview.show" v-bind:currentTab="currentTab" v-bind:icons='icons' v-bind:resume="resume" v-bind:show='preview' />
    <Preview v-show="!preview.show" v-bind:resume='resume' v-bind:show='preview' />
  </div>
</template>

<script>
  import Nav1 from './components/Nav1'
  import Editor from './components/Editor'
  import Preview from './components/Preview'
  import AV from 'leancloud-storage'

  var APP_ID = 'VY7qo7LPaz8hXMTKfuDJmLzx-gzGzoHsz';
  var APP_KEY = 'EPqpohCLQs7y4SeXdkWiROFt';

  AV.init({
    appId: APP_ID,
    appKey: APP_KEY
  });


export default {
  name: 'app',
  components: {
    Nav1,Editor,Preview
  },
  data(){
      return {
          currentTab:{
              tab:0
          },
        preview:{
              show:true
        },
        icons:['user','gongwenbao','xueshimao','skill','xiangmu']
        ,
        resume:{
          profile:{
              name:'',height:'',education:'',workDirection:'',email:'',number:'',age:'',website:'',imageUrl:'',address:'',summary:''
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
