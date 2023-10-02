<script setup lang="ts">

import useMyFetch from "~/composables/useMyFetch";

const config = useRuntimeConfig()
const { data: artists, pending } = await useMyFetch("artist",{})
// console.log(artists.value)
</script>

<template>
  <h1>Artists</h1>
  <div v-if="pending"><p>Loading...</p></div>
  <div v-else>
    <div class="mx-8 my-2 border p-4 rounded-xl hover:bg-green-200"
         v-for="artist in artists" :key="artist.id">
      <nuxt-link class="hover:text-blue-500 hover:font-bold"
                 :to="`/artists/${artist.id}`">
        {{ artist.name }}
      </nuxt-link>
    </div>
  </div>

</template>

<style scoped>

</style>