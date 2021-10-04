<template>
    <header>
        <img :src="logo" alt="Logo app">
        <div>
            <label for="selectGenre">Select genre</label>
            <select name="selectGenre" id="selectGenre" v-model="genreSelected" @change="$emit('currentGenre', genreSelected)">
                <option value="">All genre</option>
                <option v-for="(genre, index) in albumGenre" :key="index" :value="genre">{{genre}}</option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            genreSelected: ''
        }
    },
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

    label {
        margin-right: .3125rem;
        color: #fff;
    }

    select {
        padding: .625rem .9375rem;
        border-radius: .625rem;
        background-color: $colorBgBody;
        color: #fff;
    }
}
</style>