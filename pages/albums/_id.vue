<template>
  <div class="container">
    <div class="columns top-space">
      <div class="column">
        <h3 class="title">{{album.title}}</h3>
      </div>
      <div class="column is-text-right">
        <nuxt-link class="button is-primary" to="/">Back</nuxt-link>
      </div> 
    </div>
    
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
        <img :src="photo.url" :alt="photo.title">
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import env from '../../config/env'

export default {
  name: 'Album',
  data() {
    return {
      album: {},
      photos: []
    }
  },
  created() {
    let albumId = this.$route.params.id
    axios.get(`${env.endpoint}/albums/${albumId}`)
    .then(response => {
      this.album = response.data
    })

    axios.get(`${env.endpoint}/albums/${albumId}/photos`)
    .then(photoRes => {
      this.photos = photoRes.data
    })
  }
}
</script>

<style scoped>
.top-space {
  margin-top: 50px;
}
.title {
  text-transform: capitalize;
}
.is-text-right {
  text-align: right;
}
</style>
