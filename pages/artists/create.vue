<script setup lang="ts">

import useMyFetch from "~/composables/useMyFetch";

const formData = ref({
  name: ""
})

const formErrors = ref({
    errors: null
})

async function onSubmit() {
    const {name} = formData.value
    console.log(name)

  const config = useRuntimeConfig()

    const {data: response, error} = await useMyFetch<any>(
        "artist",{
            method: "POST",
            body: {name}
        }
    )

    if (response.value === null) {
        console.log(error)
        const { message } = error.value!.data
        formErrors.value.errors = message
    } else {
        await navigateTo(`/`)
    }
}
</script>

<template>

    <h1 class="text-3xl">
      Add Artist
    </h1>

    <form @submit.prevent="onSubmit()" class="m-4" action="">
      <div class="flex">
        <label for="name">Artist Name</label>
        <p class="text-red-600"
           v-if="formErrors.errors">
          {{ formErrors.errors }}
        </p>
        <input class="border border-gray-400 p-2 ml-2 rounded-xl"
               v-model="formData.name"
               placeholder="Artist name"
               type="text" id="name">
      </div>
      <div class="mt-4">
        <button class="px-4 py-2 border bg-blue-300"
                type="submit">
          Submit
        </button>
      </div>
    </form>
</template>

<style scoped>

</style>