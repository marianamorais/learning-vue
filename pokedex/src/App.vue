<template>
  <div id="app">
    <div class="column is-half is-offset-one-quarter">
      <img src="./assets/pokemon.png" alt="Pokemon logo">
      <hr>
      <h4 class="is-size-2">Pokedex</h4>
      <div id="search">
        <input type="text" name="" placeholder="Search pokemons" v-model="search" class="input">
        <button class="button is-success" id="searchBtn" @click="searchPokemon">Search</button>
      </div>
      <div v-for="(poke, index) in pokemons" :key="poke.url">
        <Pokemon :name="poke.name" :url="poke.url" :num="index+1"/>
      </div>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from './components/Pokemon';

export default {
  name: 'App',
  data() {
    return {
      pokemons: [],
      filteredPokemons: [],
      search: ''
    }
  },

  created: function() {
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res => {
      console.log("taked the list!");
      this.pokemons = res.data.results;
      this.filteredPokemons = res.data.results;
    })
  },

  components:{
    Pokemon
  },

  methods:{
    searchPokemon: function(){
      this.filteredPokemons = this.pokemons;
      if(this.search == '' || this.search == ' '){
        this.filteredPokemons = this.pokemons;
      } else {
        this.filteredPokemons = this.pokemons.filter(pokemon => pokemon.name == this.search);
      }
    }
  },

  computed: {
    // resultSearch: function(){
    //   if(this.search == '' || this.search == ' '){
    //     return this.pokemons;
    //   } else {
    //     return this.pokemons.filter(pokemon => pokemon.name == this.search)
    //   }
    // }
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

#search {
  display: flex;
  flex-direction: row;
}

#searchBtn {
  margin-left: 30px;
}
</style>