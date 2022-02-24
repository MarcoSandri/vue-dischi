<template>
    <header>
        <img src="../assets/img/logo.svg">
        <select name="genres" id="genres" @change="getValue">
            <option value = "All">All</option>
            <option v-for="(genre,index) in genreList" :key="index" :value="genre" > {{genre}} </option>
        </select>
    </header>
</template>

<script>
export default {
    name: "HeaderComponent",
    data() {
        return{
            selected : "All"
        }
    },
    props: {
        genreList : Array
    },
    methods: {
        getValue() {
           this.selected = document.getElementById("genres").value;
           console.log("Il valore selezionato è "+this.selected);

           this.$emit('sendValue', this.selected)
        }
    },
    mounted() {
        
        this.selected = document.getElementById("genres").value;
        this.$emit('sendValue', this.selected)
    }
}
</script>

<style lang="scss">
    @import "../assets/style/colors.scss";

    header {
        background-color: $secondary;
        padding: 1rem 1.5rem;
        display: flex;
        justify-content: space-between;

        img {
            width: 3rem;
        }
    }

</style>