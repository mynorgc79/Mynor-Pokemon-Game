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
        showPokemon: false
      }
    },
    methods: {
      async mixPokemonArray() {
        this.pokemonArr = await getPokemonOptions()

        const rndInt = Math.floor( Math.random() * 4 )

        this.pokemon = this.pokemonArr[rndInt]
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
    <PokemonOptions :pokemons="pokemonArr"/>
  </div>
</template>

<style>

</style>