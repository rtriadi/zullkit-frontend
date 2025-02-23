<script setup>
import { ref } from "vue";

const props = defineProps({
  galleries: Array,
});

const activeImage = ref(props.galleries[0].url);

function mouseOverGallery(image) {
  this.activeImage = image;
}
</script>
<template>
  <section id="gallery">
    <img :src="activeImage" alt="" class="w-full mt-6 rounded-2xl" />
    <div class="grid grid-cols-4 gap-4 mt-4">
      <template v-for="gallery in galleries" :key="gallery.id">
        <div
          :class="{
            'ring-2 ring-indigo-500': activeImage === gallery.url,
          }"
          class="overflow-hidden cursor-pointer rounded-2xl"
        >
          <img
            :src="gallery.url"
            class="w-full"
            alt=""
            @mouseover="mouseOverGallery(gallery.url)"
          />
        </div>
      </template>
    </div>
  </section>
</template>
