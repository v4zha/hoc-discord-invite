<template>
  <header>
    <div class="d-flex justify-content-center">
      <div class="d-flex flex-column justify-content-center">
        <h1 class="header">Hour Of Code</h1>
      </div>
      <img class="logo" src="../assets/logo.svg" alt="logo" />
    </div>
  </header>
</template>
<script>
export default {
  name: "HocHeader",
};
</script>
<style scoped>
.header {
  /* font-family: ; */
  color: #738adb;
  text-align: center;
  vertical-align: middle;
  font-family: "Roboto Mono", monospace;
}
.logo {
  width: 8%;
}
</style>
