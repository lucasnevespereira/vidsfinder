<template>
  <ul class="list-group">
    <VideoListItem 
    v-for="v in videosArray" 
    v-bind:video="v" 
    :key="v.etag" 
    @videoSelect="onVideoSelected"
    >  
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
  props: ['videosArray'],
  methods: {
    onVideoSelected(video){
      this.$emit('videoSelected', video)
    }
  }
}
</script>

<style>

</style>