<script lang="ts">

    import type { ListPokemonOptions } from '@/interfaces/ListPokemonOptions.interface';
    
    export default{
        props: {
            pokemons:{
                type:Array<ListPokemonOptions>,
                    required:true,
            }
        },
        methods: {
            hola(){

            }
           
        }
    }
</script>
<template>
    <div class="options-container">
        <ul>
        <li v-for="pokemon in pokemons" 
        :key="pokemon.id"
        @click="$emit('selection',pokemon.id)"
        class="pokemon-item"
        >
   
        
            {{ pokemon.name }} 
         </li>
        
        </ul>
    </div>
</template>

<style scoped>
    ul{
        list-style-type: none;
    }
    li{
        background-color: white;
        border-radius: 5px;
        border: 1px solid rgba(0, 0, 0, 0.2);
        cursor: pointer;
        margin-bottom: 10px;
        width: 250px;

    }
    li:hover{
        background-color: rgba(0, 0, 0, 0.05);
    }

    .options-container {
        display: flex;  
        justify-content: center;

    }

    .pokemon-item {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  cursor: pointer;
  margin-bottom: 10px;
  width: 250px;
  background: linear-gradient(to right, #a9ac1a, rgba(11, 150, 62, 0.653));/* Fondo predeterminado */
  color: white; /* Color de texto predeterminado */
  font-family: 'Montserrat', sans-serif; /* Cambia la fuente aquí */
  font-size: 16px;


}
.pokemon-item:hover {
    background: linear-gradient(to right,  gold, gold); /* Fondo al pasar el cursor */
  color: black; /* Color de texto al pasar el cursor */
}




    
</style>
