<template>
    <div class="col-md-8" v-if="video">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl" frameborder="0"></iframe>
        </div>
        <div class='details'>
            <h4>{{video.snippet.title}}</h4>
            <p>{{video.snippet.description}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'VideoDetails',
        props: ['video'],
        computed: {
            videoUrl(){
                return `https://www.youtube.com/embed/${this.video.id.videoId}`;
            }
        }
    }
</script>

<style>
.details{
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #dddddd;
    border-radius: 5px;
}
</style>
