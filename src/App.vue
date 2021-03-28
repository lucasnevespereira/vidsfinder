<template>
  <div>
    <div class="container text-center p-2">
      <h1>VidsFinder</h1>
    </div>
    <div class="container">
    <SearchBar @termChange="onTermChange" /> 
    <VideoList v-bind:videosArray="videos" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList"
const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
  },
  data() {
    return {
      videos: [],
    };
  },
  methods: {
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
