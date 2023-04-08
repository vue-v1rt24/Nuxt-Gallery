<script setup lang="ts">
const props = defineProps<{
  currentImg: string;
  timeAnimation: number;
}>();

//
const bgo = ref<HTMLDivElement | null>(null);
let setIdx: number;

//
watch(
  () => props.currentImg,
  () => {
    clearTimeout(setIdx);
    bgo.value?.classList.add('gAnim');

    setIdx = setTimeout(() => {
      bgo.value?.classList.remove('gAnim');
    }, props.timeAnimation);
  },
);
</script>

<template>
  <div class="bigGallery" ref="bgo">
    <img class="bigGallery__img" :src="currentImg" alt="" />
  </div>
</template>

<style lang="css" scoped>
.bigGallery {
  position: relative;
  height: 400px;
}

.gAnim {
  animation: op v-bind(timeAnimation + 'ms') ease-in;
}

@keyframes op {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.bigGallery__img {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 8px;
}
</style>
