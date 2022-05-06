<template>
    <div class="card-container justify-content-center">
        <img :src="item.poster" :alt="item.title">
        <h4>{{item.title}}</h4>
        <p>{{item.author}} <br> {{item.year}} </p>
    </div>
  
</template>

<script>
export default {
    name: "AppCard",
    props:{
        item:Object
    }
}
</script>

<style lang="scss" scoped>
@import "./src/style/generals.scss";
.card-container{
    padding: 14px;
    background-color: $bg-header;
    height: 350px;
    text-align: center;
    img{
    width:100%;
    }
    h4{
        color: $text-color;
        text-transform: uppercase;
        font-size: 18px;
        font-weight: 700;
        padding-top: 5px;
    }
}
p{
    color: $subtitle-color;
}
</style>