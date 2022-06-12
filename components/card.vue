<script setup>
const props = defineProps({
  pokemon: String,
});
const pok = toRef(props, 'pokemon');

const {
  data: pokemonData,
  pending,
  refresh,
  error,
} = await useFetch(`https://pokeapi.co/api/v2/pokemon/${pok.value}`);

watch(pok, () => {
  console.log(pok);
  refresh();
});
</script>

<template>
  <div v-if="pending">Loading ...</div>
  <div v-else>
    <div class="card">
      <div class="image">
        <img :src="pokemonData.sprites.front_default" alt="" />
      </div>
      <div class="content">
        <h1 class="name">{{ pokemonData.name }}</h1>
        {{ pokemon }}
        {{ pok }}
      </div>
    </div>
  </div>
</template>

<style>
.card {
  border-radius: 10px;
  background: #fff;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
}
</style>
