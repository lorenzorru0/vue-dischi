<template>
    <header>
        <img :src="logo" alt="Logo app">
        <div>
            <label for="selectGenre">Select genre</label>
            <select name="selectGenre" id="selectGenre" v-model="genreSelected" @change="$emit('currentGenre', genreSelected)">
                <option value="">All genre</option>
                <option v-for="(genre, index) in albumGenre" :key="index" :value="genre">{{genre}}</option>
            </select>
            <label for="selectAuthor">Select Authors</label>
            <select name="selectAuthor" id="selectAuthor" v-model="authorSelected" @change="$emit('currentAuthor', authorSelected)">
                <option value="">All authors</option>
                <option v-for="(author, index) in albumAuthors" :key="index" :value="author">{{author}}</option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            genreSelected: '',
            authorSelected: ''
        }
    },
    props: {
        logo: String,
        albumGenre: Array,
        albumAuthors: Array
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
        margin: {
            right: .625rem;
            left: .9375rem
        }
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