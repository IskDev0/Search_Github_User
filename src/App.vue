<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheInput from "./components/TheInput.vue";
import {ref} from "vue";
import UserCard from "./components/UserCard.vue";
import TheLoader from "./components/TheLoader.vue";
import EmptySection from "./components/EmptySection.vue"
import NotFound from "./components/NotFound.vue";

let info = ref()

let isLoaded = ref(false)

let hasError = ref(false)

let getData = (data) => {
  try {
    hasError.value = false
    isLoaded.value = true
    info.value = data.value
    console.log(info.value)
  } catch (e) {
    console.error(e)
  } finally {
    isLoaded.value = false
  }
}

let showError = () => {
  hasError.value = true
}

</script>

<template>
  <div class="wrapper bg-[#141C2F] text-white h-screen dark:text-black dark:bg-slate-100">
    <TheHeader/>
    <main class="main container mx-auto px-4 sm:px-10">
      <TheInput @error="showError" @send="getData"/>
      <UserCard v-if="info && !hasError" :info="info"/>
      <EmptySection v-else-if="!info && !hasError"/>
      <TheLoader v-if="isLoaded"/>
      <NotFound v-if="hasError"/>
    </main>
  </div>
</template>
