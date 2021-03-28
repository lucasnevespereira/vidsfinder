<template>
  <div>
    <div class="container text-center p-2">
      <h1>VidsFinder</h1>
    </div>
    <div class="container">
    <SearchBar @termChange="onTermChange" /> 
    <VideoDetail v-bind:video="selectedVideo" />
    <VideoList @videoSelected="onVideoSelect" v-bind:videosArray="videos" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";
const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onVideoSelect(video){
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        });
    },
  },
};
</script>
