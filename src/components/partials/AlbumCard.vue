<template>
  <div class="albumCard">
      <img :src="image" :alt="title">
      <h2>{{title}}</h2>
      <div class="artist">{{artist}}</div>
      <div class="year">{{year}}</div>
  </div>
</template>

<script>
export default {
    name: "AlbumCard",
    props : {
        image : String,
        title : String,
        artist : String,
        year : String,
    }
}
</script>

<style lang="scss">

    @import '../../assets/style/colors.scss';

    .albumCard {
        background-color: $secondary;
        padding: 1rem;
        color: $label;
        margin: 1rem 0;
        text-align: center;
        
        img {
            width: 175px;
        }

        h2 {
            text-transform: uppercase;
            margin: 1rem 0;
            width: 175px;
            color: $tertiary;
        }
    }
</style>