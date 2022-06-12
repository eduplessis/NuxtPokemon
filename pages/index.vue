<template>
  <div class="container">
    <card v-if="selectedPokemon" :pokemon="selectedPokemon" />
    <div v-if="pokemons" v-for="pokemon in pokemons.results">
      <button class="btn" @click="selectedPokemon = pokemon.name">
        {{ pokemon.name }}
      </button>
    </div>

    <!-- <card /> -->
  </div>
</template>
<script setup>
const selectedPokemon = ref('');
const { data: pokemons } = await useFetch(
  'https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0'
);
</script>

<style>
body {
}
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
.btn {
  display: inline-block;
  outline: none;
  text-decoration: none;
  padding: 0.8rem 1.2rem;
  border: 1px solid purple;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
  border-radius: 0.3rem;
}
.btn:hover {
  background: pink;
  color: purple;
}
</style>
