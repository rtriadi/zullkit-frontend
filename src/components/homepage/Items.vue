<script setup>
import { ref } from "vue";
import ItemCard from "@/components/ItemCard.vue";
const items = ref([
  {
    title: "Mobile UI Kit",
    image: "items-1.jpg",
    category: "Mobile UI Kit",
  },
  {
    title: "Online Doctor Consultation",
    image: "items-2.jpg",
    category: "Website UI Kit",
  },
  {
    title: "Banking Crypto",
    image: "items-3.jpg",
    category: "Mobile UI Kit",
  },
]);
</script>
<template>
  <div class="container px-4 mx-auto my-16 md:px-12">
    <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
    <div class="flex flex-wrap -mx-1 lg:-mx-4">
      <ItemCard
        v-for="item in items"
        :key="item.title"
        :title="item.title"
        :image="item.image"
        :category="item.category"
      />
    </div>
  </div>
</template>
