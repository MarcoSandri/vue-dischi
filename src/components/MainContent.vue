<template>
  <main>
      <div class="container">
          <AlbumCard v-for="(album, index) in albumList" :key="index" :image="album.poster" :title="album.title" :artist="album.author" :year="album.year"/>
      </div>
  </main>
</template>

<script>
const axios = require('axios').default;
import AlbumCard from './partials/AlbumCard.vue'

export default {
    name : "MainContent",
    components : {
        AlbumCard
    },
    data() {
        return {
            albumList : []
        }
    },
    methods : {
        getAlbums() {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                // handle success
                this.albumList = response.data.response
                console.log(response.data.response);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            });
        }
    },
    mounted() {
        this.getAlbums();
    }
}
</script>

<style lang="scss">
    @import "../assets/style/colors.scss";

    main {
        display: flex;
        align-items: center;

        .container {
            margin: auto;
            width: 60%;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
    }
</style>