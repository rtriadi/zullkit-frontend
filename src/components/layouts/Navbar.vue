<script setup>
import { onMounted, computed } from "vue";
import { useUserStore } from "@/stores/user";
import Logo from "./Logo.vue";
import NavigationLink from "./NavigationLink.vue";
import AuthButton from "./AuthButton.vue";
import UserInfo from "./UserInfo.vue";

const userStore = useUserStore();
const user = computed(() => userStore.getUser);
const isLoggedIn = computed(() => userStore.isLoggedIn);
onMounted(() => {
  userStore.fetchUser();
});
console.log(userStore);
</script>
<template>
  <nav
    class="bg-white border-gray-200 px-2 sm:px-4 py-2.5 rounded dark:bg-gray-800"
  >
    <div
      class="container flex flex-wrap items-center justify-between mx-auto my-2"
    >
      <Logo />
      <UserInfo :user="user.data" v-if="isLoggedIn" />
      <AuthButton v-else />
      <div
        class="items-center justify-between hidden w-full md:flex md:w-auto md:order-1"
        id="mobile-menu-2"
      >
        <ul
          class="flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-regular"
        >
          <li>
            <NavigationLink to="/">Home</NavigationLink>
          </li>
          <li>
            <NavigationLink to="/categories">Categories</NavigationLink>
          </li>
          <li>
            <NavigationLink to="/pricing">Pricing</NavigationLink>
          </li>
          <li>
            <NavigationLink to="#">Study Case</NavigationLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
