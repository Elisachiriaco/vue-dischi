<template>
<section class="container">
    <app-loader v-if="loading"/>
    <!-- author: (…)
        genre: (…)
        poster: (…)
        title: (…)
        year: (…) -->
    <div class="row justify-content-center p-4">
        <div class="col-6 col-sm-4 col-md-2 m-2"
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
        setTimeout(()=>{
            this.loading = true;
            axios.get(this.api).then((res)=>{
            this.songList = res.data.response;
            this.loading = false
            console.log(this.songList)
        }).catch((error) => {
            console.log(error)
            this.loading = false;
        })
     },1000)
    }
}
</script>

<style lang="scss">
@import "./src/style/generals.scss";

</style>