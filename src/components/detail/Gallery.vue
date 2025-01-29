<script setup>
import { ref } from "vue";
const galleries = ref([
  {
    id: 1,
    image: "gallery-2.png",
  },
  {
    id: 2,
    image: "gallery-3.png",
  },
  {
    id: 3,
    image: "gallery-4.png",
  },
  {
    id: 4,
    image: "gallery-5.png",
  },
]);
//make a function to make active gallery
const activeImage = ref("gallery-2.png");

function mouseOverGallery(image) {
  this.activeImage = image;
}
</script>
<template>
  <section id="gallery">
    <img
      :src="'../src/assets/img/' + activeImage"
      alt=""
      class="w-full mt-6 rounded-2xl"
    />
    <div class="grid grid-cols-4 gap-4 mt-4">
      <template v-for="gallery in galleries" :key="gallery.id">
        <div
          :class="{
            'ring-2 ring-indigo-500': activeImage === gallery.image,
          }"
          class="overflow-hidden cursor-pointer rounded-2xl"
        >
          <img
            :src="'../src/assets/img/' + gallery.image"
            class="w-full"
            alt=""
            @mouseover="mouseOverGallery(gallery.image)"
          />
        </div>
      </template>
    </div>
  </section>
</template>
