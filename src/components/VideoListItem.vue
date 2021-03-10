<template>
    <div>
        <li class="list-group-item media" @click="onVideoClick">
            <img class="mr-3" :src="thumbnailUrl" />
            <div class="media-body">
                {{ oneVideo.snippet.title }}
            </div>
        </li>
    </div>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['oneVideo'],

    methods: {
        onVideoClick(){
            this.$emit('videoClicked', this.oneVideo)
        }
    },

    computed: {
        thumbnailUrl() {
            return this.oneVideo.snippet.thumbnails.default.url
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
        background-color: #eee;
    }

</style>