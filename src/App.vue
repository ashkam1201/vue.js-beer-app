<template>
  <div id="beerCall">
    <button @click="apiCall">A selection of quality beers</button>
    <div v-for="(beer, index) in result.data" :key="index">
      {{beer.name}}
    </div>
  </div>

</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      result: []
    }
  },
  methods: {
    async apiCall() {
      try {
        const axios = require ('axios')
        this.result = await axios.get('https://api.punkapi.com/v2/beers?brewed_before=11-2012&abv_gt=6')
        console.log("Data fetched", this.result);
      }catch (e) {
        console.error(e)
      }
      
      
      
      

    }
  }
}
</script>

<style>

button{
  font-family: "American Typewriter";
}
#beerCall{
  font-family:  'Hoefler Text', Georgia, 'Times New Roman', serif;
  font-weight: normal;
  line-height: 35px;
  margin-left: auto;
  margin-right: auto;
  width: 6em
}
</style>
