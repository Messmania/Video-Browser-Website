<template>
    <div v-if="video" class="embed-responsive embed-responsive-16by9">
        <iframe class="embed-responsive-item" :src="videoURL"/>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoURL(){
            const videoId  = this.video.id.videoId;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>

<style scoped>


iframe {
    width: 100%;
    height: 100%;
}
</style>