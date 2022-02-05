<template>
  <div class="app d-flex flex-column">
    <hoc-header />
    <hoc-join />
    <hoc-footer />
  </div>
</template>

<script>
import HocHeader from "./components/HocHeader.vue";
import HocFooter from "./components/HocFooter.vue";
import HocJoin from "./components/HocJoin.vue";
export default {
  name: "App",
  components: {
    HocHeader,
    HocJoin,
    HocFooter,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@500&family=Roboto+Mono:wght@500&display=swap");
#app {
  text-align: center;
  /* margin-top: 60px; */
  margin-top: 2%;
}
html,
body {
  background-color: #23272a;
}
.app {
  background: #23272a;
}
</style>
