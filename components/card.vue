<script setup>
const props = defineProps({
  pokemon: Object,
});
</script>

<template>
  <div class="card">
    <div class="image"></div>
    <div class="content">
      <div class="name">{{ pokemon.name }}</div>
    </div>
  </div>
</template>


<style >

</style>