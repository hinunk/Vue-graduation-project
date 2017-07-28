<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
    <Topbar class="topbar" v-on:preview="preview"/>
    <div class="main">
      <Editor v-bind:resume="resume" class="editor" />
      <Preview v-bind:resume="resume" class="preview" />
    </div>
     <el-button id="exitPreview" v-on:click="exitPreview">退出预览</el-button>
  </div>
</template>

<script>
import Editor from './components/Editor'
import Preview from './components/Preview'
import Topbar from './components/Topbar'
export default {
  data() {
    return {
      previewMode: false,
      resume: {
        formLabelAlign: {
          name: '',
          location: '',
          birth: ''
        },
        workExperience: [
          {
            company: '',
            jobContent: ''
          }
        ],
        schoolExperience: [
          {
            school: '',
            degree: '',
            time: ''
          }
        ],
        projects: [
          {
            name: '',
            content: ''
          }
        ],
        awards: [
          {
            name: ''
          }
        ],
        contacts: {
          qq: '',
          wechat: '',
          phone: '',
          email: ''
        }
      }
    }
  },
  methods:{
      exitPreview(){
        this.previewMode = false
      },
      preview(){
        this.previewMode = true
      }
  },
  components: {
    Editor,
    Preview,
    Topbar
  },
}
</script>

<style lang="scss">
html,
body,
#app {
  height: 100%;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.icon {
  width: 2.5em;
  height: 2.5em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

.topbar {
  -webkit-box-shadow: 0 10px 6px -6px #777;
  -moz-box-shadow: 0 10px 6px -6px #777;
  box-shadow: 0 10px 6px -6px #777;
  position: relative;
  z-index: 1;
}

.main {
  display: flex;
  flex: 1;
  background: #ddd;
  >.editor {
    min-width: 40em;
    margin: 16px 8px 16px 16px;
    background: white;
    -webkit-box-shadow: 0 10px 6px -6px #777;
    -moz-box-shadow: 0 10px 6px -6px #777;
    box-shadow: 0 10px 6px -6px #777;
  }

  >.preview {
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: white;
    -webkit-box-shadow: 0 10px 6px -6px #777;
    -moz-box-shadow: 0 10px 6px -6px #777;
    box-shadow: 0 10px 6px -6px #777;
  }
}
.previewMode > #topbar{
  display: none;
}
.previewMode #editor{
  display: none;
}
.previewMode #preview{
  max-width: 800px;
  margin: 32px auto;
}
#exitPreview{
  display: none;
}
.previewMode #exitPreview{
  display: inline-block;
  position: fixed;
  right: 16px;
  bottom: 16px;
}
</style>
