<script setup>
import { ref } from "vue";
import CategoryCard from "./../CategoryCard.vue";
const Categories = ref([
  { id: 1, title: "Mobile UI Kit", image: "categories-1.jpg", count: "731" },
  { id: 2, title: "Fonts", image: "categories-2.jpg", count: "65" },
  { id: 3, title: "Icon Set", image: "categories-3.jpg", count: "83,559" },
  {
    id: 4,
    title: "Website UI Kits",
    image: "categories-4.jpg",
    count: "4,500",
  },
]);
</script>
<template>
  <div class="container px-4 mx-auto my-16 md:px-12" id="categories">
    <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">Top Categories</h2>
    <div class="flex flex-wrap -mx-1 lg:-mx-4">
      <CategoryCard
        v-for="category in Categories"
        :key="category.id"
        :title="category.title"
        :image="category.image"
        :count="category.count"
      />
    </div>
  </div>
</template>
