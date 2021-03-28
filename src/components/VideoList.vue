<template>
  <ul class="list-group">
    <VideoListItem v-for="v in videosArray" v-bind:video="v" :key="v.etag">
      
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem"
export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: ['videosArray']
}
</script>

<style>

</style>