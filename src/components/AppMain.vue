<template>
<section class="container">
    <app-search v-if="!loading" @performSearch="mySearch" :songGenere="genere"/>
    <app-loader v-if="loading"/>
    <!-- author: (…)
        genre: (…)
        poster: (…)
        title: (…)
        year: (…) -->
    <div class="row justify-content-center p-4">
        <div class="col-6 col-sm-4 col-md-2 m-2"
        v-for="(song, index) in filteredList" :key="index">
        <app-card :item="song"/>
        </div>
    </div>
</section>
  
</template>

<script>
import AppLoader from './AppLoader.vue'
import axios from 'axios';
import AppCard from './AppCard.vue';
import AppSearch from './AppSearch.vue';

export default {
    name: "AppMain",
    components: { 
        AppLoader,
        AppCard,
        AppSearch
    },
    data(){
        return {
            songList:[],
            searchText:'',
            api:'https://flynn.boolean.careers/exercises/api/array/music',
            loading: true,
            genere: [],
        }
    },
    methods:{
        mySearch(text){
            this.searchText = text;
        }
    },
    computed:{
        filteredList(){
            if(this.searchText ==='') {
                return this.songList;
            }

            return this.songList.filter((el)=> {
                return el.genre === this.searchText;
            });
        },
        
    },
    mounted(){
        setTimeout(()=>{
            this.loading = true;
            axios.get(this.api).then((res)=>{
            this.songList = res.data.response;
            this.songList.forEach((el)=>{
                if(!this.genere.includes(el.genre)){
                    this.genere.push(el.genre);
                }
            })
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

</style>