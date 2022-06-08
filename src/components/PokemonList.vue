<script setup>
import { ref, onMounted, reactive } from "vue";
import axios from "axios";
import PokemonItem from "./PokemonItem.vue";

const state = reactive({
  pokemons: [],
});

onMounted(() => {
  getPokemons();
});

async function getPokemons() {
  const limit = 20;
  try {
    const pokemons = await axios.get(
      `https://pokeapi.co/api/v2/pokemon?limit=${limit}`
    );
    if (pokemons.data.results) {
      const pokemonsMap = pokemons.data.results.map(async (item) => {
        const responseItem = await axios.get(item.url);

        if (responseItem.data) {
          return {
            ...item,
            ...responseItem.data,
          };
        }
      });

      const pokemonsData = await Promise.all(pokemonsMap);

      state.pokemons = pokemonsData;
    }
  } catch (error) {
    console.log(error);
  }
}
</script>

<template>
  <div class="pokemon-list">
    <div v-for="pokemon in state.pokemons" :key="pokemon.name">
      <div>
        <PokemonItem :pokemon="pokemon" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.pokemon-list {
  padding: 1rem;
  display: grid;
  grid-gap: 2rem 2rem;
  grid-template-columns: repeat(auto-fill, 250px);
}
</style>
