<template>
  <div>
    <Header :logo="require('./assets/img/spotify-logo.png')" :albumGenre='albumGenre' :albumAuthors='albumAuthors' @currentGenre='getCurrentGenre' @currentAuthor='getCurrentAuthor' />
    <AlbumContainer @emitAlbumGenre='getAlbumGenre' @emitAlbumAuthors='getAlbumAuthors' :currentGenre='currentGenre' :currentAuthor='currentAuthor' />
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
      albumAuthors: [],
      currentGenre: '',
      currentAuthor: ''
    }
  },
  methods: {
    getAlbumGenre(genres) {
      this.albumGenre = genres;
    },
    getAlbumAuthors(authors) {
      this.albumAuthors = authors;
    },
    getCurrentGenre(currentGenre) {
      this.currentGenre = currentGenre;
      console.log(this.currentGenre);
    },
    getCurrentAuthor(currentAuthor) {
      this.currentAuthor = currentAuthor;
      console.log(this.currentAuthor);
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
