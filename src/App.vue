<template>
  <div class="column-flex">
    <div class="header">
      <div class="left">Video browser</div>
      <div class="right"> Created by: Monika Sahai </div>
    </div>
    <div class="row-flex">
      <div>
        <img class="video-icon" src="./images/circle_icon.png" height="50px" />
        <!-- <img src="./images/green_icon.png" height="55px" /> -->
      </div>
      <div class="full-width">
        <SearchBar @searchTermChange="onTermChange"></SearchBar>
        <div class="my-flex">
          <VideoDetail :video="selectedVideo" />
          <VideoList :myVideos="videos" @videoSelect="onVideoSelect"></VideoList>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"; //--for HTTP requests
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

const API_KEY = "AIzaSyBPJd5gzE9sjlQHstfyGpi58nUcm9hA2j0";

export default {
  name: "App",
  data() {
    return { videos: [], selectedVideo: null };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(results => {
          console.log("Video results:", results.data.items);
          this.videos = results.data.items;
        });
    }
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  }
};
</script>

<style>
body {
  font-family: sans-serif;
  height: 100vh;
}

.header {
  border-bottom: 2px solid teal;
  background-color: #2580008a;
  display: flex;
  justify-content: space-between;
  padding: 10px;
}

.left {
  line-height: 37px;
  font-size: 25px;
}

.right {
  line-height: 37px;
  /* font-style: italic; */
}

.video-icon {
  height: 50px;
  margin-top: 16px;
}

.my-flex {
  display: flex;
  margin: 20px;
}

.column-flex {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.row-flex {
  display: flex;
  justify-content: center;
  padding: 10px 0;
  height: 100%;
  background-color: #75cd3212;
}

.full-width {
  width: 50%;
}
</style>