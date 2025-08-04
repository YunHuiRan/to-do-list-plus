<template>
  <div class="flex-box flex-col bg-blue-500 w-full h-full">
    <!-- name -->
    <div class="flex-box relative w-full h-1/2 z-0 bg-amber-300">
      <span class="absolute top-0.5 select-none z-[-1]">your name here!</span>

      <input class="opacity-80 border-2" />
    </div>

    <!-- password -->
    <div class="flex-box relative w-full h-1/2">2</div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const nameInputFocused = ref(false);
const passwordInputFocused = ref(false);
</script>

<style></style>
