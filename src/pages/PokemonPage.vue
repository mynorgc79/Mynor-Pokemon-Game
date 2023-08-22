<script lang="ts">

  import PokemonOptions from '@/components/PokemonOptions.vue'
  import PokemonPicture from '@/components/PokemonPicture.vue'
  import getPokemonOptions from '@/helpers/getPokemonOptions'
  import type { ListPokemonOptions } from '@/interfaces/ListPokemonOptions.interface'


  export default {
    components: { PokemonOptions, PokemonPicture },
    data() {
      return {
        pokemonArr: [] as ListPokemonOptions[],
        pokemon: null as ListPokemonOptions | null,
        showPokemon: false,
        showAnswer: false,
        message: ''
      }
    },
    methods: {
      async mixPokemonArray() {
        this.pokemonArr = await getPokemonOptions()

        const rndInt = Math.floor( Math.random() * 4 )

        this.pokemon = this.pokemonArr[rndInt]
      },
      checkAnswer( selectedId:number){
        //console.log('llamada desde el PokemonPage', pokemonId)
         this.showPokemon = true;
         this.showAnswer = true;
         this.pokemonArr = []

         if(!this.pokemon) return;
         if (selectedId === this.pokemon?.id){
            this.message = `correcto, ${this.pokemon.name}`
         }else{
          this.message = `Oops, era ${this.pokemon.name}`
         }
      },

      newGame(){
        this.showPokemon = false,
        this.showAnswer =  false,
        this.pokemonArr = [],
        this.pokemon = null,
        this.mixPokemonArray()
      }

    },
    mounted() {
      this.mixPokemonArray()
    }
  }
</script>

<template>
  <h1 v-if="!pokemon">Espere por favor...</h1>

  <div v-else>
    <h1>¿Quién es este pokémon?</h1>
  
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
    <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer"/>

     <div v-if="showAnswer">
        <h2 class="fade-in">{{ message}}</h2>
       <button @click="newGame" class="dual-color-button">
       Nuevo Juego
       </button>
     </div>
</div>
</template>

<style scoped>
  .dual-color-button {
  background: linear-gradient(to right, #ff5733, #33ffbb); /* Cambia los colores según tus preferencias */
  color: white; /* Cambia el color del texto para que sea legible */
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}
</style>