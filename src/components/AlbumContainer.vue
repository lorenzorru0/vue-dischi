<template>
    <section>
        <div class="container">
            <Album v-for="(album, index) in albums" :key="index" :album="album"/>
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
            albums: []
        }
    },
    created() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then( (res) => {
                this.albums = res.data.response;
                console.log(this.albums)
            });
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variable.scss';

section {
    background-color: $colorBgBody;
    padding: 3.125rem 0;

    .container {
        display: flex;
        flex-wrap: wrap;
    }
}
</style>