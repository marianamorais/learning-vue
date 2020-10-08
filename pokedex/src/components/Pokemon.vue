<template>
  <div id="pokemon">
    <h1></h1>
    <div class="card">
      <div class="card-image">
        <figure>
          <img
            :src="currentImg"
            alt="Pokemon"
            @click="changeSprite"
          />
        </figure>
      </div>
      <div class="card-content">
        <div class="media">
          <div class="media-content">
            <p class="title is-4">{{ num }} - {{ name }}</p>
            <p class="subtitle is-6">{{ pokemon.type  }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  created: function() {
    axios.get(this.url).then((res) => {
      this.pokemon.type = res.data.types[0].type.name;
      this.pokemon.front = res.data.sprites.front_default;
      this.pokemon.back = res.data.sprites.back_default;
      this.currentImg = this.pokemon.front;
    });
  },

  data() {
    return {
      isFront: true,
      currentImg: '',
      pokemon: {
        type: '',
        front: '',
        back: '',
      },
    };
  },

  props: {
    num: Number,
    name: String,
    url: String,
  },

  methods: {
    changeSprite: function() {
      if(this.isFront){
        this.isFront = false;
        this.currentImg = this.pokemon.back;
      } else {
        this.isFront = true;
        this.currentImg = this.pokemon.front;
      }
    }
  }
};
</script>

<style>
  #pokemon {
    margin-top: 2%;
  }
</style>
