<template>
  <div class="flex m-8 justify-between w-1/2">
    <UseStateCounter @changeUp="onChangeUp" @changeDown="onChangeDown"
                     name="reactive First">

    </UseStateCounter>
    <UseStateCounter @changeUp="onChangeUp" @changeDown="onChangeDown"
                     name="reactive Second">

    </UseStateCounter>
    <UseStateCounter @changeUp="onChangeUp" @changeDown="onChangeDown"
                     name="reactive Third">

    </UseStateCounter>
  </div>

  <div>
    Message : {{ message }} <br>
    AppTheme : {{ appTheme}} <br>
  </div>
</template>
<script setup lang="ts">
import { useLocalStorage, useSessionStorage } from '@vueuse/core'
import RefCounter from "~/components/RefCounter.vue";
import ReactiveCounter from "~/components/ReactiveCounter.vue";
import UseStateCounter from "~/components/UseStateCounter.vue";

const message = ref("")
const appTheme = useLocalStorage('nuxt-color-mode', null)
const hello = useSessionStorage('hello', null)
function onChangeUp(name: string, count: number) {
  message.value = `Counter ${name} has been changed up to ${count}`
}

function onChangeDown(name: string, count: number) {
  message.value = `Counter ${name} has been changed down to ${count}`
}

</script>