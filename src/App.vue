<template>
    <div class="container">
        <SearchBar @termChange="onTermChange" ></SearchBar>
        <div class="row align-items-start">
            <div class="col">
            <VideoDetail :video="selectedVideo" ></VideoDetail>
            </div>

            <div class="col">
            <VideoList :retrievedVideos="videos" @selectedVideo="displayVideo"></VideoList>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = 'AIzaSyAxOw85SA_LxOpAWYCR9fNpFV--N73TLwY';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() {
        return { videos: [], selectedVideo: null };
    },
    methods: {
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            })
            .then(response => {
                this.videos = response.data.items;
            });
        },

        displayVideo(video){
            this.selectedVideo = video;
        },
    },
};
</script>