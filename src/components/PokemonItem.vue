<script setup>
import { computed } from "@vue/runtime-core";

const props = defineProps(["pokemon"]);

const pokemonTypes = computed(() => {
  return props.pokemon.types.map((type) => type.type.name).join(", ");
});
</script>

<template>
  <div class="item">
    <div class="image">
      <img
        :src="pokemon.sprites.other['official-artwork'].front_default"
        :alt="pokemon.name"
        width="100"
      />
    </div>
    <div class="info">
      <h3>
        {{ pokemon.name }}
      </h3>
      <p>
        {{ pokemonTypes }}
      </p>
    </div>
  </div>
</template>

<style scoped>
.item {
  background-color: #f2f2f2;
  overflow: hidden;
  position: relative;
  padding: 8px;
  font-family: "Roboto";
}

.item .image {
  text-align: center;
}

.item .info {
  padding: 8px;
}

.item .info h3,
p {
  padding: 0;
  margin: 0;
}
.item .info p {
  font-size: 0.8rem;
  color: #999;
}
</style>
