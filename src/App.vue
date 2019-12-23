<template>
  <div id="app">
  <home></home>
    <router-view/>
  </div>
</template>
<script>
  import Home from "./views/Home";
  export  default {
    components:{
      Home
    }
  }
</script>
<style lang="less">

</style>
