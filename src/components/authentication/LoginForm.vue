<script setup>
import { ref } from "vue";
import Input from "@/components/Input.vue";
import axios from "axios";
import { useUserStore } from "@/stores/user";
import { useRouter } from "vue-router";

const userStore = useUserStore();
const router = useRouter();

const form = ref({
  email: "",
  password: "",
});

async function login() {
  try {
    const response = await axios.post("http://127.0.0.1:8000/api/login", {
      email: form.value.email,
      password: form.value.password,
    });
    localStorage.setItem("access_token", response.data.data.access_token);
    localStorage.setItem("token_type", response.data.data.token_type);
    userStore.fetchUser();
    router.push("/");
    console.log(response.data);
  } catch (error) {
    console.error(error);
  }
}
</script>

<template>
  <form>
    <Input
      v-model="form.email"
      label="Email Address"
      placeholder="Type your email"
      id="email"
      type="email"
      name="email"
    />
    <Input
      @keyup.enter="login"
      v-model="form.password"
      label="Password"
      placeholder="Type your password"
      id="password"
      type="password"
      name="password"
    />
    <div class="mt-6">
      <button
        @click="login"
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
