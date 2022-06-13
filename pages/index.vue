<template>
  <div class="container">
    <div
      v-if="selectedPokemon"
      class="container-over"
      @click="selectedPokemon = ''"
    >
      <card v-if="selectedPokemon" :pokemon="selectedPokemon" />
    </div>

    <div v-if="pokemons" v-for="pokemon in pokemons.results">
      <button class="btn" @click="selectedPokemon = pokemon.name">
        {{ pokemon.name }}
      </button>
    </div>
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

.container-over {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  background: rgba(0, 0, 0, 0.2);
  align-items: center;
  justify-content: center;
}
</style>
