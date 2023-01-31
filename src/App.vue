<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheInput from "./components/TheInput.vue";
import {ref} from "vue";
import UserCard from "./components/UserCard.vue";

let info = ref()

let getData = (data) => {
  info.value = data.value
  console.log(info.value)
}

</script>

<template>
  <div class="wrapper bg-[#141C2F] text-white h-screen">
    <TheHeader/>
    <main class="main container mx-auto">
      <TheInput @send="getData"/>
      <UserCard v-if="info" :info="info" />
    </main>
  </div>
</template>
