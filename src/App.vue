<template>
  <div>
    <Header/>
    <AlbumContainer/>
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
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
