<script setup lang="ts">
import { IGallery } from '~~/types/IGallery.types';

const props = defineProps<{
  photos: IGallery[];
  imgIndex: number;
}>();

//
const previewList = ref<HTMLUListElement | null>(null);

//
watch(
  () => props.imgIndex,
  () => {
    previewList.value &&
      (previewList.value.style.transform = `translateX(-${
        props.imgIndex * 160
      }px)`);
  },
);
</script>

<template>
  <div class="preview">
    <ul class="preview__list" ref="previewList">
      <li v-for="photo in photos" :key="photo.id" class="preview__item">
        <img :src="photo.src" alt="" />
      </li>
    </ul>

    <div class="preview__active">{{ imgIndex + 1 }} / {{ photos.length }}</div>
  </div>
</template>

<style lang="css" scoped>
.preview {
  position: relative;
  width: 470px;
  margin: 0 auto;
  overflow: hidden;
}

.preview__list {
  position: relative;
  left: 160px;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  transition: transform 0.3s;
}

.preview__item {
  width: 150px;
  border-radius: 8px;
  overflow: hidden;
}
.preview__active {
  position: absolute;
  inset: 0 0 0 50%;
  transform: translateX(-50%);
  width: 150px;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
