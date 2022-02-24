<template>
  <main>
      <div class="container">
          <AlbumCard v-for="(album, index) in filtered" :key="index" :image="album.poster" :title="album.title" :artist="album.author" :year="album.year" />
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
    props: {
        selectedValue : String
    },
    data() {
        return {
            albumList : [],
            genres : [],
        }
    },
    methods : {
        getAlbums() {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                // handle success
                this.albumList = response.data.response
                this.getAlbumsGenre();
                console.log(response.data.response);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            });
        },

        getAlbumsGenre() {
            this.genres.push(this.albumList[0].genre);
            for(let i = 0; i < this.albumList.length; i++) {

                if(!this.genres.includes(this.albumList[i].genre)) {
                    
                    this.genres.push(this.albumList[i].genre);
                }
            }

            console.log(this.genres);
            this.$emit('getGenres', this.genres);
        },

        
    },
    mounted() {
        this.getAlbums();
    },
    computed: {

        filtered() {
            return this.albumList.filter((album) => {
                if(this.selectedValue != "All") {
                    if(album.genre == this.selectedValue) {
                        return true;
                    }
                    return false;
                }
                else return true;
            })
        }

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
            justify-content: space-around;
        }
    }
</style>