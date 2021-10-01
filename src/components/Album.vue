<template>
    <div class="album">
        <img :src="album.poster" :alt="album.author + album.title">
        <h2>{{album.title}}</h2>
        <p>{{album.author}}</p>
        <p>{{album.year}}</p>
    </div>
</template>

<script>
export default {
    name: 'Album',
    props: ['album']
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variable.scss';

.album {
    width: $widthAlbum;
    margin: 1.25rem;
    padding: 1.25rem;
    background-color: $colorBgHeader;

    img {
        width: 100%;
    }

    h2 {
        padding: 1.25rem 0;
        text-align: center;
        color: #fff;
        text-transform: uppercase;
    }

    p {
        text-align: center;
        color: #808080;
        font-size: 1.2rem;
    }
}
</style>