<template>
  <div class="flex-box relative bg-blue-300 w-full h-full">
    <div
      class="flex-box flex-col bg-red-300 relative w-[25%] h-[50%] min-w-[500px] min-h-[450px] rounded-2xl shadow-[10px_10px_0px_-1px_rgba(0,0,0,0.5)]"
    >
      <!-- title -->
      <div class="flex-box w-[90%] h-[10%] bg-amber-700 text-3xl">welcome!</div>

      <!-- log in or register form -->
      <div class="flex-box w-[90%] h-[50%] bg-emerald-500">
        <component :is="forms[currentForm]" />
      </div>

      <!-- form switch button -->
      <div class="flex-box w-[90%] h-[20%] bg-amber-700">
        <!-- toggle between log in and register forms -->
        <span v-if="currentForm === 'logIn'"
          >on account? click
          <a @click="toggleForm" class="text-white cursor-pointer">HERE</a>
          to register
        </span>

        <span v-else>
          already have an account? click
          <a @click="toggleForm" class="text-white cursor-pointer">HERE</a>
          to log in
        </span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineAsyncComponent, ref } from "vue";

const WelcomeLogInForm = defineAsyncComponent(
  () => import("./components/WelcomeLogInForm.vue")
);
const WelcomeRegisterForm = defineAsyncComponent(
  () => import("./components/WelcomeRegisterForm.vue")
);

const currentForm = ref("logIn");
const toggleForm = () => {
  currentForm.value = currentForm.value === "logIn" ? "register" : "logIn";
};

const forms = {
  logIn: WelcomeLogInForm,
  register: WelcomeRegisterForm,
};
</script>

<style></style>
