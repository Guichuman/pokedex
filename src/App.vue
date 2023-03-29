<template>
  <div id="app">
    <figure class="" >
      <img src="./assets/logo_pokemon.png" id="logo-img">
    </figure>
    <hr>
    <div class="column is-half is-offset-one-quarter">
      <input type="text" class="input is-rounded " name="" placeholder="Search pokemon by full name" v-model="search">
      <div v-for="(poke, index) in searchResult" :key="index"> 
        <Pokemon :name="poke.name" :url="poke.url" :num="index+1" />
      </div>
    </div>

    </div>
</template>

<script>
import axios from 'axios'
import Pokemon from './components/MyPokemon.vue'



export default {
  name: 'App',
  data(){
    return {
      pokemons: [],
      search : ''
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res => {
      this.pokemons = res.data.results
    })
  },
  components:{
    Pokemon
  },
  computed: {
    searchResult: function(){
      if(this.search == '' || this.search == ' '){
        return this.pokemons
      }else{
        return this.pokemons.filter(pokemon => pokemon.name == this.search)
      }
    }
  }
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#logo-img{
  height: 20%;
  width: 40%;
}

#searchBtn{
  margin-top: 2%
  
}
</style>
