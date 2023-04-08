<script setup lang="ts">
import { IGallery } from '~~/types/IGallery.types';

const props = withDefaults(
  defineProps<{
    photos: IGallery[];
    timeAnimation?: number;
  }>(),
  {
    timeAnimation: 500,
  },
);

//
const imgIndex = ref(0);

//
const currentImg = computed(() => props.photos[imgIndex.value]);
const prevImg = computed(() => props.photos[imgIndex.value - 1]);
const nextImg = computed(() => props.photos[imgIndex.value + 1]);
</script>

<template>
  <div>
    <GalleryBigImg
      :current-img="currentImg.src"
      :time-animation="timeAnimation"
    />

    <GalleryArrow
      @prev-click="imgIndex--"
      @next-click="imgIndex++"
      :prev-disabled="!prevImg"
      :next-disabled="!nextImg"
      :time-animation="timeAnimation"
    />

    <GalleryPreview :photos="photos" :img-index="imgIndex" />
  </div>
</template>

<style lang="css" scoped></style>
