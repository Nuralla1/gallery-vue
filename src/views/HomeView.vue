<script setup>
import Search from "../components/Search.vue";
import ImageList from "../components/ImageList.vue";
import { provide, ref } from "vue";

const searchValue = ref("");

const imgs = ref([]);

function updateImgs(arg) {
  imgs.value = arg;
}

provide("gallery", {
  searchValue,
  imgs,
  updateImgs,
});
</script>

<template>
  <main>
    <Search />
    <ImageList />
  </main>
</template>

<style scoped></style>
