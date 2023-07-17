<script setup>
import { RouterView } from "vue-router";
import Header from "./components/Header.vue";
import { provide, ref } from "vue";
import mock from "./assets/mock.png";

const favs = ref([]);

const addToFavs = (newValue) => {
  const hasMatch = favs.value.some(
    (item) => item?.urls?.regular === newValue?.urls?.regular
  );
  if (!hasMatch) {
    favs.value.push(newValue);
  }
};

const removeFromFavs = (newValue) => {
  favs.value = favs.value.filter(
    (item) => item?.urls?.regular != newValue?.urls?.regular
  );
};

provide("favs", {
  favs,
  addToFavs,
  removeFromFavs,
});
</script>

<template>
  <Header />
  <RouterView />
</template>

<style scoped></style>
