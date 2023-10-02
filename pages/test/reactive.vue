<script setup lang="ts">

import ReactiveCounter from "~/components/ReactiveCounter.vue";
import {ref, reactive} from "vue";
const messager = ref({info : ""})
</script>

<template>
<div class="flex m-8 justify-between w-1/2">
  <ReactiveCounter name="1"></ReactiveCounter>
  <ReactiveCounter name="2"></ReactiveCounter>
  <ReactiveCounter name="3"></ReactiveCounter>
</div>
</template>

<style scoped>

</style>