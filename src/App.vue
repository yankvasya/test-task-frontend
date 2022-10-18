<template>
  <div class="wrapper">
    <CustomList
      :list="selectedItems"
      :maxLimit="limitSelectedItems"
      @update:element="changeSelectedItems"
    />
    <CustomSelected :item="selectedItem" @delete:element="deleteSelectedItem" />
    <CustomList :list="left" @update:element="addSelectedItems" />
    <CustomList :list="right" @update:element="changeSelectedItem" />
  </div>
</template>

<script setup>
import CustomList from "./components/CustomList.vue";
import CustomSelected from "./components/CustomSelected.vue";
import { ref } from "vue";

const left = [
  {
    id: 1,
    name: "Shoes 1",
  },
  {
    id: 2,
    name: "Shoes 2",
  },
  {
    id: 3,
    name: "Shoes 3",
  },
  {
    id: 4,
    name: "Shoes 4",
  },
  {
    id: 5,
    name: "T-shirt 1",
  },
  {
    id: 6,
    name: "T-shirt 2",
  },
  {
    id: 7,
    name: "T-shirt 3",
  },
  {
    id: 8,
    name: "T-shirt 4",
  },
];
const right = [
  {
    id: 11,
    name: "Jacket 1",
  },
  {
    id: 12,
    name: "Jacket 2",
  },
  {
    id: 13,
    name: "Jacket 3",
  },
  {
    id: 14,
    name: "Jacket 4",
  },
  {
    id: 15,
    name: "Hoodie 1",
  },
  {
    id: 16,
    name: "Hoodie 2",
  },
  {
    id: 17,
    name: "Hoodie 3",
  },
  {
    id: 18,
    name: "Hoodie 4",
  },
];

const limitSelectedItems = 6;
const selectedItems = ref([]);
const addSelectedItems = (value) => {
  if (selectedItems.value.length >= limitSelectedItems) {
    // удаление первого товара
    selectedItems.value.shift();
  }
  selectedItems.value.push(value);

  // если нужно запретить добавление элементов при переполнении лимита, заменить на:
  // if (selectedItems.value.length < limitSelectedItems) {
  // selectedItems.value.push(value);
  // }
};
const changeSelectedItems = (value) => {
  // FIXME: реализовать удалению по клику на определенный элементы
  // filter, slice польностью ломают возможно работы с массивом
  // удаление последнего товара
  selectedItems.value.pop();
};

const selectedItem = ref({});
const changeSelectedItem = (value) => (selectedItem.value = value);
const deleteSelectedItem = () => (selectedItem.value = {});
</script>

<style scoped src="./styles/app.scss" lang="scss" />
