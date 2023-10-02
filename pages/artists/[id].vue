<script setup lang="ts">
import useMyFetch from "~/composables/useMyFetch";
const rounte = useRoute()
const pageTitle = `Artist ID: ${rounte.params.id}`
const {data:artist, error} = await useMyFetch(
    `artist/${rounte.params.id}`,{})
if (artist.value === null) {
  const {statusCode, statusMessage} = error.value
  console.log(statusCode,statusMessage)
}


console.log(rounte.params)
</script>

<template>
<div>Artist No. {{ rounte.params.id }}</div>
  <div>
    {{artist}}
  </div>

  <div>
    {{error}}
  </div>
</template>

<style scoped>

</style>