<script setup lang="ts">
import { useAuthStore } from '~/stores/useAuthStore'
const auth = await useAuthStore()
const errorMessage = ref<string|undefined>("")

const formData = reactive({
  email: "",
  password: ""
})

async function onSubmit() {

  // const {email, password} = formData
  // console.log(email, password)
  const email = formData.email
  const pass = formData.password
  const {data: response, error} = await useMyFetch<any>(
      "auth/login", {
        method: "POST",
        body: formData
      }
  )
  if (response.value === null) {
    errorMessage.value = error.value?.data.message
  } else {
    const {access_token, token_type } = response.value
    if (access_token !== "") {
      auth.setNewToken(access_token)
      await navigateTo("/playlist")
    }
  }
}
// import useMyFetch from "~/composables/useMyFetch";
// import {useAuthStore} from "~/stores/useAuthStore";
// const auth = await useAuthStore
// const formData = ref({
//   email: "",
//   pass: ""
// })
//
// const formErrors = ref({
//   errors: null
// })
//
// async function onSubmit() {
//
//   const {email} = formData.value
//   const {pass} = formData.value
//   console.log([email, pass])
//
//   // const config = useRuntimeConfig()
//
//   const {data: response, error} = await useMyFetch<any>(
//       "auth/login",{
//         method: "POST",
//         body: {
//           "email" : email,
//           "password" : pass
//         }
//       }
//   )
//
//   if (response.value === null) {
//     console.log(error)
//     const { message } = error.value!.data
//     formErrors.value.errors = message
//   } else {
//     const { access_token, token_type } = response.value
//     auth.setNewToken(access_token)
//     // await navigateTo(`/`)
//   }
// }
</script>

<template>
  <form @submit.prevent="onSubmit()" class="container mx-auto p-4 mt-12 bg-white flex flex-col items-center justify-center text-gray-700">
    <div class="w-10/12 sm:w-8/12 md:w-6/12 lg:w-5/12 xl:w-4/12 mb-4">
      <h1 class="text-4xl font-semibold">Welcome</h1>
    </div>
    <div class="w-10/12 sm:w-8/12 md:w-6/12 lg:w-5/12 xl:w-4/12 mb-6">
      <input class="mb-4 p-2 appearance-none block w-full bg-gray-200 placeholder-gray-900 rounded border focus:border-teal-500"
             type="text"
             v-model="formData.email"
             id="email"
             placeholder="Email"
      />
      <input class="mb-4 p-2 appearance-none block w-full bg-gray-200 placeholder-gray-900 rounded border focus:border-teal-500"
             type="password"
             v-model="formData.password"
             id="password"
             placeholder="Password"
      />
      <div class="flex items-center">
        <button class="ml-auto w-1/2 bg-gray-800 text-white p-2 rounded font-semibold hover:bg-gray-900" type="submit">Log In</button>
      </div>
    </div>
  </form>
</template>

<style scoped>

</style>