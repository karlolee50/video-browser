<template>
    <div>
        <ul class="list-group">
        <VideoListItem 
            v-for="retrievedVideo in retrievedVideos" 
            :key="retrievedVideo.id.videoId"
            :oneVideo="retrievedVideo"
            @videoClicked="videoSelected">
        </VideoListItem>
        </ul>
    </div>
</template>

<script>
import VideoListItem from './VideoListItem';


export default {
    name: 'VideoItem',
    components: {
        VideoListItem
    },
    props: ['retrievedVideos'],

    methods: {
        videoSelected(video) {
            this.$emit('selectedVideo', video);
        }
    }
}
</script>

<style>

</style>