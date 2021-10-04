<template>
  <div>
    <Header :logo="require('./assets/img/spotify-logo.png')" :albumGenre='albumGenre' @currentGenre='getCurrentGenre'/>
    <AlbumContainer @emitAlbumGenre='getAlbumGenre' :currentGenre='currentGenre'/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import AlbumContainer from './components/AlbumContainer.vue'


export default {
  name: 'App',
  components: {
    Header,
    AlbumContainer
  },
  data() {
    return {
      albumGenre: [],
      currentGenre: ''
    }
  },
  methods: {
    getAlbumGenre(genres) {
      this.albumGenre = genres;
    },
    getCurrentGenre(currentGenre) {
      this.currentGenre = currentGenre;
      console.log(this.currentGenre);
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
