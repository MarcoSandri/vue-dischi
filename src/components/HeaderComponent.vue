<template>
    <header>
        <img src="../assets/img/logo.svg">
    </header>
</template>

<script>
export default {
    name: "HeaderComponent"
}
</script>

<style lang="scss">
    @import "../assets/style/colors.scss";

    header {
        background-color: $secondary;
        padding: 1rem 1.5rem;

        img {
            width: 3rem;
        }
    }

</style>