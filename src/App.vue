<template>
  <div id="app">
    <AppHeader />
    <main>
      <AppMain />
    </main>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain  
  }
}
</script>

<style lang="scss">
@import "./style/generals.scss";
@import "./style/vars.scss";

</style>
