<script setup>
import Home from "./views/Home.vue";
</script>

<template>
  <Home />
</template>

<style>
@font-face {
  font-family: "Roboto";
  src: local("Roboto"),
    url(./assets/fonts/Roboto/Roboto-Regular.ttf) format("truetype");
}

html,
body {
  margin: 0;
}

header {
  background-color: #212121;
  color: #fff;
  padding: 0.5rem 1rem;
  text-align: center;
}

.container {
  max-width: 960px;
  margin-left: auto;
  margin-right: auto;
}
</style>
