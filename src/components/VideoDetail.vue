<template>
  <div v-if="video">
    Video Detail
    {{video.snippet.title}}
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"]
  
}
</script>
