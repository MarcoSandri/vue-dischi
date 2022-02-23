<template>
  <div id="app">
    <HeaderComponent />
    <MainContent class="main"/>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainContent
  }
}
</script>

<style lang="scss">
  @import "./assets/style/colors.scss";
  @import "./assets/style/general.scss";

  #app {
    display: flex;
    flex-direction: column;
    height: 100vh;

    .main {
      flex: 1 1 0;
    }
  }
</style>
