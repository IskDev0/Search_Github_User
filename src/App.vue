<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheInput from "./components/TheInput.vue";
import {ref} from "vue";

let info = ref()

let getData = (data) => {
  info.value = data.value
}

</script>

<template>
  <div class="wrapper bg-[#141C2F] text-white">
    <TheHeader/>
    <main class="main container mx-auto">
      <TheInput @send="getData"/>

    </main>
  </div>
</template>
