<template>
  <div class="column is-one-quarter">
    <div class="box">
      <h3>{{album.title | capitalize}}</h3>
      <nuxt-link class="button is-primary" :to="`/albums/${album.id}`">View album</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AlbumCard',
  props: {
    album: Object
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style scoped>
.box {
  padding: 1em;
}
h3 {
  min-height: 5em;
}
</style>
