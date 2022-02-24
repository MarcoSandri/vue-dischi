<template>
  <div id="app">
    <HeaderComponent :genreList="genres" @sendValue="printValue"/>
    <MainContent class="main" @getGenres="printGenres" :selectedValue="selectedValue"/>
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
  },
  data() {
    return {
      genres : [],
      selectedValue : ""
    }
  },
  methods : {
    printGenres(allGenres) {
      this.genres = allGenres;
      console.log("i generi nell'app sono: " + this.genres)
    },
    printValue(selected) {
      this.selectedValue = selected;
      console.log("IL VALORE SELEZIONATO SULL'APP è : " + this.selectedValue)
    }
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
