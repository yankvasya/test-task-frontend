<template>
  <div class="container">
    <ul class="list">
      <li v-for="e of currentArray" :key="e.key" class="list__element">
        <CustomElement :element="e" @update:element="updateElement" />
      </li>
    </ul>

    <div v-if="maxLimit" class="limits">
      Selected: {{ slicedArray.length }}/{{ maxLimit }}
    </div>
  </div>
</template>

<script setup>
import CustomElement from "./CustomElement.vue";
import { computed } from "vue";

const { list, maxLimit } = defineProps({
  list: {
    type: Array,
    default: [],
  },
  maxLimit: {
    type: Number,
  },
});

const emit = defineEmits(["update:element"]);

// slicedArray, можно использовать для принудительного изменения длины массива
const slicedArray = computed(() => list.slice(-1 * maxLimit));

const currentArray = maxLimit ? slicedArray : list;

console.log(currentArray);
console.log(maxLimit);

const updateElement = (e) => emit("update:element", e);
</script>

<style scoped lang="scss">
.container {
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  border: 3px solid black;
  padding: 5px;

  .list {
    display: flex;
    gap: 10px;
  }
}
</style>
