<template>
    <div>
        <SearchBar @searchInputChanged="searchInputChanged"></SearchBar>
    </div>
</template>

<script>
    import axios from 'axios';
    import SearchBar from './components/SearchBar';
    const API_KEY = 'AIzaSyBvGkNP_EehunNwkRS6r0chhyOhb2YnWpo';

    export default{
        name: 'App',
        components: {
            SearchBar
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
                }).then((res) => console.log(res)).catch((err) => console.log('Could no t find results'));
            }
        }
    };
</script>

<style>

</style>
