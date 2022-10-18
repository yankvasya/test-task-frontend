<template>
  <a @click.prevent="clickElement()" href="#" class="element">
    {{ element.name }}
  </a>
</template>

<script setup>
const { element } = defineProps({
  element: {
    type: Object,
  },
});

const emit = defineEmits(["update:element"]);

const clickElement = () => emit("update:element", element);
</script>

<style scoped lang="scss">
.element {
  display: inline-flex;
  border: 4px solid black;
  padding: 3px;
  transition: 0.2s all;

  &:hover {
    transform: scale(1.2);
    transition: 0.3s all;
  }
}
</style>
