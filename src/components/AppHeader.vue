<template>
  <header>
    <img src="../assets/logo.png" alt="">
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
  props: {

  }
}
</script>

<style scoped lang="scss">
@import "./src/style/vars.scss";

header{
  background-color: $bg-header;
  height: 60px;
  img{
    padding: 10px;
    width: 60px;
    height: 60px;
  }
}
</style>
