<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheInput from "./components/TheInput.vue";
import {ref} from "vue";
import UserCard from "./components/UserCard.vue";
import TheLoader from "./components/TheLoader.vue";

let info = ref()

let isLoaded = ref(false)

let getData = (data) => {
  try {
    isLoaded.value = true
    info.value = data.value
    console.log(info.value)
  } catch (e) {
    console.error(e)
  } finally {
    isLoaded.value = false
  }
}

</script>

<template>
  <div class="wrapper bg-[#141C2F] text-white h-screen">
    <TheHeader/>
    <main class="main container mx-auto">
      <TheInput @send="getData"/>
      <UserCard v-if="info" :info="info"/>
      <TheLoader v-if="isLoaded"/>
    </main>
  </div>
</template>
