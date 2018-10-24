<template>
  <div>
    <h1>Albums de la página</h1>
    <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
  </div>
</template>

<script>
import axios from 'axios'
import env from '../config/env'
import AlbumCard from '../components/AlbumCard'

export default {
  name: 'IndexPage',
  components: {
    AlbumCard
  },
  data() {
    return {
      albums: []
    }
  },
  created() {
    axios.get(`${env.endpoint}/albums`)
    .then(response => {
      this.albums = response.data
    })
  }
}
</script>

<style scoped>

</style>
