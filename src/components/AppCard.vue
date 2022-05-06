<template>
<div>
    <img :src="item.poster" :alt="item.title">
    <h4>{{item.title}}</h4>
    <p>{{item.author}}</p>
    <p>{{item.year}}</p>
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
img{
    width:100%;
}

</style>