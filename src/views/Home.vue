<script setup>
import PokemonList from "../components/PokemonList.vue";
</script>

<template>
  <Header />
  <div class="container">
    <div class="content">
      <PokemonList />
    </div>
  </div>
</template>

<style scoped>
.content {
  margin: 2rem 0 3rem;
}
</style>
