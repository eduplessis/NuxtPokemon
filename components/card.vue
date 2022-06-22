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
} = await useFetch(() => `/pokemon/${pok.value}`, {
  baseURL: 'https://pokeapi.co/api/v2',
});
onMounted(() => {
  refresh();
});
</script>

<template>
  <div v-if="pending">Loading ...</div>
  <div v-else>
    <div class="card">
      <div class="card-header">
        <h1 class="name">{{ pokemonData.name }}</h1>
        <div class="hp">
          {{ pokemonData.stats[0].base_stat }}
          {{ pokemonData.stats[0].stat.name }}

          allo benoit
        </div>
      </div>

      <div class="image">
        <img :src="pokemonData.sprites.front_default" alt="" />
      </div>
      <div class="content">
        {{ pokemon }}
        {{ pok }}
      </div>
    </div>
  </div>
</template>

<style>
.card {
  border: 20px solid rgb(237, 205, 60);
  border-radius: 10px;
  background: #fff;
  box-shadow: 2.2px 2.6px 0.8px rgba(0, 0, 0, 0.032),
    5.6px 6.7px 3.7px rgba(0, 0, 0, 0.04),
    11.3px 13.6px 10.7px rgba(0, 0, 0, 0.045),
    23.4px 28.1px 26.9px rgba(0, 0, 0, 0.052),
    64px 77px 80px rgba(0, 0, 0, 0.07);
  padding: 20px;
  width: 300px;
  height: 425px;
}
.card-header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: baseline;
}
.card-header .name {
  text-transform: capitalize;
}
.card-header .hp {
  font-size: 1.4rem;
}
.card .image {
  width: 100%;
  aspect-ratio: 16 / 10;
}
.card .image img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
</style>
