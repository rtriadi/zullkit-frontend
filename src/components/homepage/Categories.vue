<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";
import CategoryCard from "./../CategoryCard.vue";

const categories = ref([]);

async function getCategoriesData() {
  try {
    const response = await axios.get(
      "http://127.0.0.1:8000/api/categories?limit=4"
    );
    console.log(response.data);
    categories.value = response.data.data.data;
  } catch (error) {
    console.log(error);
  }
}

onMounted(() => {
  getCategoriesData();
});
</script>
<template>
  <div class="container px-4 mx-auto my-16 md:px-12" id="categories">
    <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">Top Categories</h2>
    <div class="flex flex-wrap -mx-1 lg:-mx-4">
      <CategoryCard
        v-for="category in categories"
        :key="category.id"
        :id="category.id"
        :title="category.name"
        :image="category.thumbnails"
        :count="category.products_count"
      />
    </div>
  </div>
</template>
