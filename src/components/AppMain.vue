<template>
<section class="container">
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
import axios from 'axios';
import AppCard from './AppCard.vue'

export default {
    name: "AppMain",
    components: { 
        AppCard
    },
    data(){
        return {
            songList:[],
            api:'https://flynn.boolean.careers/exercises/api/array/music',
            loading:false
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
        })
    } 
}
</script>

<style lang="scss" scoped>
@import "./src/style/generals.scss";

section{
    padding: 50px 0px;
}
</style>