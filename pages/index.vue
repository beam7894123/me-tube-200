<script setup lang="ts">

import Counter from "~/components/Counter.vue";
import RefCounter from "~/components/RefCounter.vue";
</script>

<template>
  <Counter :name="`Main`"></Counter>
  <RefCounter :name="`Ref`"></RefCounter>
<h1>AAAAAA</h1>

  <img src="@/assets/images/1cbb069a4b41d527f24f26a86658049f90e5576164171f6bb8c99e2d542ecf9d.png" class="w-48">
  <hr class="my-8">
  <img src="/images/2ed9068cb95b6276d9c808ae9c2a4d20bb415f45dd132dd5aee1209425bc1218.png" class="w-72">
</template>

<style scoped>

</style>