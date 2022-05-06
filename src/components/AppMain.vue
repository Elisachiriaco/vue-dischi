<template>
<section class="container">
    <app-loader v-if="loading"/>
    <!-- author: (…)
        genre: (…)
        poster: (…)
        title: (…)
        year: (…) -->
    <div class="row">
        <div class="col-6 col-md-2 m-3"
        v-for="(song, index) in songList" :key="index">
        <app-card :item="song"/>
        </div>
    </div>
</section>
  
</template>

<script>
import AppLoader from './AppLoader.vue'
import axios from 'axios';
import AppCard from './AppCard.vue'

export default {
    name: "AppMain",
    components: { 
        AppLoader,
        AppCard
    },
    data(){
        return {
            songList:[],
            api:'https://flynn.boolean.careers/exercises/api/array/music',
            loading: true,
        }
    },
    mounted(){
        this.loading = true;
            axios.get(this.api).then((res)=>{
            this.songList = res.data.response;
            this.loading = false
            console.log(this.songList)
        }).catch((error) => {
            console.log(error)
            this.loading = false;
        })
    } 
}
</script>

<style lang="scss">
@import "./src/style/generals.scss";

section{
    padding: 50px 0px;
}
</style>