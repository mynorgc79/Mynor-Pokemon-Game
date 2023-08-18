<script lang="ts">

    import pokemonOptions from '@/components/PokemonOptions.vue';
    import PokemonPicture from '@/components/PokemonPicture.vue';
    import pokemonPicture from '@/components/PokemonPicture.vue';
    import getPokemonOptions from '@/helpers/getPokemonOptions'

    console.log(getPokemonOptions());

    export default {

        components: { pokemonOptions,
    pokemonPicture, PokemonPicture }

    }
</script>

<template>
    <h1> ¿Quien es este pokemon? </h1>

    <PokemonPicture  :pokemonId="18" :showPokemon="true" />
    <pokemonOptions/>
</template>

<style >

</style>