<template>
  <div id="app">
    <ApiSearch/>
  </div>
</template>

<script>
import ApiSearch from "./components/ApiSearch.vue";

export default {
  name: "app",
  components: {
    ApiSearch
  }
};
</script>

<style lang="less">
@import "./less/app.less";
</style>
