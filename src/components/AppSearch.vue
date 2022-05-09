<template>
  <div>
    <select name="genere" id="genere" v-model="inputText" @change="changeSearch">
        <option value="">Scegli un genere:</option>
        <option value="">All</option>
        <option :value="genre" v-for="(genre, index) in songGenere" :key="index">{{genre}}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'InputApp',
  data(){
      return {
          inputText: '',
      }
  },
  props:['songGenere'],
  methods: {
    changeSearch() {
      this.$emit('performSearch', this.inputText)
    }
  }
}
</script>

<style lang="scss">
select {
    position: absolute;
    top: 20px;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 250px;
    text-align: center;
}
</style>
