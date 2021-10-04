<template>
  <div>
    <Header :logo="require('./assets/img/spotify-logo.png')" :albumGenre='albumGenre'/>
    <AlbumContainer @emitAlbumGenre='getAlbumGenre' />
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
      albumGenre: []
    }
  },
  methods: {
    getAlbumGenre(genres) {
      this.albumGenre = genres;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
