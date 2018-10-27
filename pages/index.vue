<template>
  <div class="container">
    <h1 class="title">Albums de la página</h1>
    <div class="columns is-multiline">
      <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
    </div>
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
  async asyncData ({ req, res }) {
    let { data } = await axios.get(`${env.endpoint}/albums`)
    return { albums: data }
  }
}
</script>

<style scoped>
h1 {
  padding-top: 20px;
  padding-bottom: 15px;
}
</style>
