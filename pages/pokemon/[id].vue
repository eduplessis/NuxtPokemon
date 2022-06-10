<script setup>
const route = useRoute();
// const { pending, data: count } = useLazyAsyncData('count', () =>
//   $fetch('/api/count')
// );
</script>

<template>
  {{ route.params.id }}
  {{ route.params.url }}
</template>
