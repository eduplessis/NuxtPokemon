<template>
  <div v-for="pokemon in pokemons.results">
    <NuxtLink
      :to="{
        name: 'pokemon-id',
        params: { id: pokemon.name, url: pokemon.url },
      }"
      >{{ pokemon.name }}</NuxtLink
    >
    {{ pokemon }}
  </div>
</template>
<script setup>
const { data: pokemons } = await useFetch(
  'https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0'
);
</script>
