<template>
  <a @click.prevent="clickElement()" href="#" class="selected-item" v-if="item">
    {{ item.name }}
  </a>
</template>

<script setup>
const { item } = defineProps({
  item: {
    type: Object,
  },
});

const emit = defineEmits(["delete:element"]);

const clickElement = () => emit("delete:element");
</script>

<style scoped lang="scss">
.selected-item {
  display: flex;
  justify-content: center;
  justify-self: right;
  align-items: center;
  width: 160px;
  height: 160px;
  border: 3px solid black;
  font-size: 25px;
}
</style>
