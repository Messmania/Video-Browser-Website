<template>
  <ul class="list-group">
    <VideoListItem v-for="v in myVideos" 
      :myVideo="v"
      :key="v.etag" 
      @videoSelect="onVideoSelect"
      >
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  props: ['myVideos'],
  methods: {
    onVideoSelect(video){
      this.$emit('videoSelect', video);
    }
  }
};
</script>

<style scoped>
.list-group {
  width: 100%;
}
</style>