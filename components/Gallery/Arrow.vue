<script setup lang="ts">
const props = defineProps<{
  prevDisabled: boolean;
  nextDisabled: boolean;
  timeAnimation: number;
}>();

const emit = defineEmits<{
  (e: 'prevClick'): void;
  (e: 'nextClick'): void;
}>();

//
const asd = ref(false);

//
const changeIndex = (num: number) => {
  if (asd.value) return;
  asd.value = true;

  if (num === -1) {
    emit('prevClick');
  } else {
    emit('nextClick');
  }

  setTimeout(() => (asd.value = false), props.timeAnimation);
};
</script>

<template>
  <div class="galWrapBtn">
    <button class="btn" :disabled="prevDisabled" @click="changeIndex(-1)">
      Назад
    </button>
    <button class="btn" :disabled="nextDisabled" @click="changeIndex(1)">
      Вперёд
    </button>
  </div>
</template>

<style lang="css" scoped>
.galWrapBtn {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin: 20px 0;
}

.btn {
  background-color: aliceblue;
  border: 1px solid rgb(215, 225, 233);
  border-radius: 8px;
  padding: 6px 10px;
  transition: 0.3s;
}

.btn:hover {
  background-color: rgb(215, 225, 233);
}

.btn:disabled {
  opacity: 0.5;
  pointer-events: none;
}
</style>
