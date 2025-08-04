<template>
  <div class="flex-box flex-col bg-blue-500 w-full h-full">
    <!-- name -->
    <div class="flex-box w-full h-1/2">
      <div class="flex-box relative w-[100%] h-[40px]">
        <label
          :class="[
            'absolute text-xl select-none transition-all duration-300 ease-in-out pointer-events-none',
            nameInputFocused || logInForm.name.length !== 0
              ? 'top-[-30px] left-4 text-base text-white'
              : 'top-2 left-1/2 text-xl text-black -translate-x-1/2',
          ]"
        >
          your name here!
        </label>

        <input
          ref="nameInputRef"
          v-model="logInForm.name"
          class="w-full h-full rounded-xl outline-none pl-4 bg-white"
          @focus="nameInputFocused = true"
          @blur="nameInputFocused = false"
        />

        <transition name="fade">
          <img
            v-if="logInForm.name.length !== 0"
            src="@/assets/clear.svg"
            alt="clear"
            class="absolute right-4 h-[80%] opacity-50 cursor-pointer select-none"
            @click="clearName"
          />
        </transition>
      </div>
    </div>

    <!-- password -->
    <div class="flex-box relative w-full h-1/2">
      <div class="flex-box relative w-[100%] h-[40px]">
        <label
          :class="[
            'absolute text-xl select-none transition-all duration-300 ease-in-out pointer-events-none',
            passwordInputFocused || logInForm.password.length !== 0
              ? 'top-[-30px] left-4 text-base text-white'
              : 'top-2 left-1/2 text-xl text-black -translate-x-1/2',
          ]"
        >
          your password here!
        </label>

        <input
          ref="passwordInputRef"
          v-model="logInForm.password"
          class="w-full h-full rounded-xl outline-none pl-4 bg-white"
          @focus="passwordInputFocused = true"
          @blur="passwordInputFocused = false"
        />

        <transition name="fade">
          <img
            v-if="logInForm.password.length !== 0"
            src="@/assets/clear.svg"
            alt="clear"
            class="absolute right-4 h-[80%] opacity-50 cursor-pointer select-none"
            @click="clearPassword"
          />
        </transition>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const nameInputRef = ref<HTMLInputElement | null>(null);
const passwordInputRef = ref<HTMLInputElement | null>(null);

const nameInputFocused = ref(false);
const passwordInputFocused = ref(false);

const logInForm = ref({
  name: "",
  password: "",
});

const clearName = () => {
  logInForm.value.name = "";
  if (nameInputRef.value) {
    nameInputRef.value.focus();
  }
};

const clearPassword = () => {
  logInForm.value.password = "";
  if (passwordInputRef.value) {
    passwordInputRef.value.focus();
  }
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease-in-out;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-to,
.fade-leave-from {
  opacity: 0.5;
}
</style>
