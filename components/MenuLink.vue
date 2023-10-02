<script setup lang="ts">
const props = defineProps([
    'to'
])

</script>

<template>
  <NuxtLink class="inline-block px-4 py-2 bg-red-300 hover:bg-blue-300" :to="to">
    <slot></slot>
  </NuxtLink>
</template>

<style scoped>

</style>