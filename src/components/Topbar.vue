<template>
    <div id="topbar">
        <div>logo</div>
        <div class="buttons">
            <button id="js-trigger-overlay" type="button">注册</button>
            <button id="js-trigger-overlay" type="button">登录</button>
            <el-button v-on:click="preview">预览</el-button>
        </div>
    </div>
</template>

<script>
  export default {
    methods:{
      preview(){
        this.$emit('preview')
      }
    }
  }
</script>

<style lang="scss">
#topbar {
    border: 1px solid black;
    padding: 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .buttons {
        display: flex;
         :nth-child(2) {}
    }
    #js-trigger-overlay {
        font-size: 1em;
        padding: 1em 1em;
        background-color: #009ac9;
        border: 1px solid transparent;
        color: #ffffff;
        font-weight: 300;
        -webkit-border-radius: 3px;
        border-radius: 3px;
        -webkit-transition: all 0.3s ease-in-out;
        -moz-transition: all 0.3s ease-in-out;
        transition: all 0.3s ease-in-out;
    }
    #js-trigger-overlay:hover {
        background-color: #ffffff;
        color: #009ac9;
        border-color: #009ac9;
    }
}
</style>
