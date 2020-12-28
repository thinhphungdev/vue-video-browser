<template>
  <div class="container">
      <h1>The Thinh Phung's Video Browser App</h1>
      <SearchBar @termChange="onTermChange" /> 
      <div class="row"> 
        <VideoDetails :video="selectedVideo" /> 
        <VideoList @videoSelect="onVideoSelect" :videos = "videos" />
      </div>
      <h4>Created by Thinh Phung. Dec, 2020</h4>
  </div> 
</template>

<script>
import SearchBar from "./components/SearchBar"
import VideoList from "./components/VideoList"
import VideoDetails from './components/VideoDetails.vue'
import axios from "axios";

const API_KEY = "YOUR_PRIVATE_API_HERE";
export default {
  name: 'App', 
  components: {
  SearchBar,
  VideoList,
  VideoDetails
  },
  data() {
    return {
       videos : [],
       selectedVideo: null
    }
  },
  methods: {
    onTermChange(searchterm) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchterm
        }
      })
      .then(response => {
         this.videos = response.data.items;
      })
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
}
// NOTE: Simple Vue app, build for fun to apply Vue knowledge in practice. 
</script>

<style>

</style>
