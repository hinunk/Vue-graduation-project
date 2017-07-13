<template>
  <div id="app">
    <Topbar class="topbar" />
    <div class="main">
      <Editor class="editor" />
      <Preview class="preview" />
    </div>
  </div>
</template>

<script>
import Editor from './components/Editor'
import Preview from './components/Preview'
import Topbar from './components/Topbar'
export default {
  components: {
    Editor,
    Preview,
    Topbar
  }
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
</style>
