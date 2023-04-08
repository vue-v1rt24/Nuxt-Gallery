<script setup lang="ts">
import { IGallery } from './types/IGallery.types';

const photos: IGallery[] = [
  { id: 1, src: '/photos/1.jpg' },
  { id: 2, src: '/photos/2.jpg' },
  { id: 3, src: '/photos/3.jpg' },
  { id: 4, src: '/photos/1.jpg' },
  { id: 5, src: '/photos/2.jpg' },
  { id: 6, src: '/photos/3.jpg' },
];
</script>

<template>
  <div class="container">
    <Gallery :photos="photos" />
  </div>
</template>

<style lang="css" scoped>
.container {
  max-width: 900px;
  font-family: sans-serif;
  padding: 50px 30px;
  margin: 0 auto;
}
</style>
