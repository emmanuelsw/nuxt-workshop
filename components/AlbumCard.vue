<template>
  <div >
    <h3>{{album.title}}</h3>
    <a href="#">Ver álbum</a>
  </div>
</template>

<script>
export default {
  name: 'AlbumCard',
  props: {
    album: Object
  }
}
</script>

<style scoped>

</style>
