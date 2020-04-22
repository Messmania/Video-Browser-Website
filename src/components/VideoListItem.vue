<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3" :src="thumbnailURL"/>
        <div class="media-body">
            {{myVideo.snippet.title}}
        </div>
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['myVideo'],
    computed: {
        thumbnailURL(){
            return this.myVideo.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onVideoSelect(){
            this.$emit('videoSelect', this.myVideo);
        }
    }
}
</script>

<style scoped>
    li {
        display: flex; 
        cursor: pointer;
    }

    li:hover {
        background-color: lightgray;
    }
</style>