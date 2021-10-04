<template>
    <header>
        <img :src="logo" alt="Logo app">
        <select name="filterGenre" id="filterGenre">
            <option value="">Select genre</option>
            <option v-for="(genre, index) in albumGenre" :key="index" :value="genre">{{genre}}</option>
        </select>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        logo: String,
        albumGenre: Array
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variable.scss';

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: $colorBgHeader;
    padding: 1.25rem 1.25rem;

    img {
        width: 4rem;
    }

    select {
        padding: .625rem .9375rem;
        border-radius: .625rem;
        background-color: $colorBgBody;
        color: #fff;
    }
}
</style>