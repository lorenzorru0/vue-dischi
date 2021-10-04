<template>
    <section>
        <div class="container">
            <Album v-for="(album, index) in albumFiltered" :key="index" :album="album"/>
            <h2 v-show="albumFiltered.length == 0">There's no album</h2>
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
            albumGenre: [],
            albumAuthors: []
        }
    },
    props: {
        currentGenre: String,
        currentAuthor: String
    }
    ,
    computed: {
        albumFiltered() {
            return this.albums.filter( (elm) => {
                if ( this.currentGenre == '' && this.currentAuthor == '' ) {
                    return true;
                } else {
                    if (elm.genre == this.currentGenre) {
                        if (this.currentAuthor == '') {
                            return true;
                        } else {
                            if (elm.author == this.currentAuthor) {
                                return true;
                            } else {
                                return false;
                            }
                        }
                    } else {
                        if (this.currentGenre == '' && elm.author == this.currentAuthor) {
                            return true;
                        }
                    }
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
                this.albums.forEach((elm) => {
                    if ( !this.albumAuthors.includes(elm.author)) { 
                        this.albumAuthors.push(elm.author);
                    }
                });
                this.$emit('emitAlbumGenre', this.albumGenre);
                this.$emit('emitAlbumAuthors', this.albumAuthors);
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

        h2 {
            margin: 0 auto;
            color: #fff;
            background-color: $colorBgHeader;
            padding: 2rem;
            border: .0625rem solid #fff;
            border-radius: 1.5625rem;
            box-shadow: 0 0 .2rem #fff;
        }
    }
}
</style>