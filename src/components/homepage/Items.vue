<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";
import ItemCard from "@/components/ItemCard.vue";
const items = ref([]);

async function getItemsData() {
  try {
    const response = await axios.get("http://127.0.0.1:8000/api/products");
    console.log(response.data);
    items.value = response.data.data.data;
  } catch (error) {
    console.log(error);
  }
}

onMounted(() => {
  getItemsData();
});
</script>
<template>
  <div class="container px-4 mx-auto my-16 md:px-12">
    <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
    <div class="flex flex-wrap -mx-1 lg:-mx-4">
      <ItemCard
        v-for="item in items"
        :key="item.id"
        :id="item.id"
        :title="item.name"
        :image="item.thumbnails"
        :category="item.category.name"
      />
    </div>
  </div>
</template>
