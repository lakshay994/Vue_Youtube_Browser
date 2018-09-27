<template>
    <div class="container">
        <SearchBar @searchInputChanged="searchInputChanged"></SearchBar>
        <div class="row">
            <VideoDetails :video="selectedVideo"></VideoDetails>
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import SearchBar from './components/SearchBar';
    import VideoList from './components/VideoList';
    import VideoDetails from './components/VideoDetails';
    const API_KEY = 'AIzaSyBvGkNP_EehunNwkRS6r0chhyOhb2YnWpo';

    export default{
        name: 'App',
        data(){
            return{
                videos: [],
                selectedVideo: null
            }
        },
        components: {
            SearchBar,
            VideoList,
            VideoDetails
        },
        methods: {
            searchInputChanged(searchTerm) {
                axios.get('https://www.googleapis.com/youtube/v3/search', {
                    params: {
                        key: API_KEY,
                        type: 'video',
                        part: 'snippet',
                        q: searchTerm
                    }
                }).then((res) => this.videos = res.data.items);
            },
            onVideoSelect(video){
                this.selectedVideo = video;
            }
        }
    };
</script>

<style>

</style>
