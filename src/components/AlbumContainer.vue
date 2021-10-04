<template>
    <section>
        <div class="container">
            <Album v-for="(album, index) in albumFiltered" :key="index" :album="album"/>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Album from './Album.vue'

export default {
    name: 'AlbumContainer',
    components: {
        Album
    },
    data() {
        return {
            albums: [],
            albumGenre: []
        }
    },
    props: ['currentGenre'],
    computed: {
        albumFiltered() {
            return this.albums.filter( (elm) => {
                if ( this.currentGenre == '' ) {
                    return true;
                } else {
                    return elm.genre == this.currentGenre;
                }
                
            });
        }
    },
    created() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then( (res) => {
                this.albums = res.data.response;
                this.albums.forEach((elm) => {
                    if ( !this.albumGenre.includes(elm.genre)) { 
                        this.albumGenre.push(elm.genre);
                    }
                });
                this.$emit('emitAlbumGenre', this.albumGenre);
            });
    },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variable.scss';

section {
    min-height: calc(100vh - 5.75rem);
    background-color: $colorBgBody;
    padding: 3.125rem 0;

    .container {
        display: flex;
        flex-wrap: wrap;
    }
}
</style>