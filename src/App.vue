<template>
  <div id="app">
    <Topbar/>
    <Editor/>
    <Preview/>
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

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
