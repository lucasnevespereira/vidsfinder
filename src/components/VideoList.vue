<template>
  <ul>
    VideoList
    {{ videosArray.length }}
  </ul>
</template>

<script>
export default {
  name: 'VideoList',
  props: ['videosArray']
}
</script>

<style>

</style>