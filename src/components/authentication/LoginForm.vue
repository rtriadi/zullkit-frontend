<script setup>
import { ref } from "vue";
import Input from "./../../Components/Input.vue";

const form = ref({
  email: "",
  password: "",
});

const submitForm = () => {
  console.log(form.value);
};
</script>

<template>
  <form @submit.prevent="submitForm">
    <Input
      v-model="form.email"
      label="Email Address"
      placeholder="Type your email"
      id="email"
      type="email"
      name="email"
    />
    <Input
      v-model="form.password"
      label="Password"
      placeholder="Type your password"
      id="password"
      type="password"
      name="password"
    />
    <div class="mt-6">
      <button
        type="button"
        class="inline-flex items-center justify-center w-full px-8 py-3 text-base font-medium text-white bg-indigo-600 border border-transparent rounded-full hover:bg-indigo-700 md:py-2 md:text-lg md:px-10 hover:shadow"
      >
        Sign In
      </button>
      <RouterLink
        to="/register"
        type="button"
        class="inline-flex items-center justify-center w-full px-8 py-3 mt-2 text-base font-medium text-black bg-gray-200 border border-transparent rounded-full hover:bg-gray-300 md:py-2 md:text-lg md:px-10 hover:shadow"
      >
        Create New Account
      </RouterLink>
    </div>
  </form>
</template>
