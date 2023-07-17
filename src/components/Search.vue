<script setup>
import { inject } from "vue";
const { searchValue, updateImgs } = inject("gallery");

const handleClick = async () => {
  const response = await fetch(
    `https://api.unsplash.com/search/photos?client_id=dhMA85RAZd4pMnpJprdOcvgMf6vMzrBH2HaV8Z4KtHM&per_page=9&query=${searchValue.value}`
  );
  const res = await response.json();
  updateImgs(res?.results);
};
</script>

<template>
  <div class="container">
    <div class="background"></div>
    <div class="search">
      <img src="../assets/search_icon.png" alt="search" @click="handleClick" />
      <input type="text" placeholder="Поиск" v-model="searchValue" />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  padding: 5rem;
}

.background {
  position: absolute;
  top: 0;
  left: 0;
  background-image: url("../assets/background.png");
  background-size: cover;
  z-index: -1;
  height: 100%;
  width: 100%;
}
.search {
  position: relative;
}

img {
  position: absolute;
  right: 10px;
  top: 12px;
  width: 20px;
}

input {
  padding: 15px 30px;
  border-radius: 2px;
  border: none;
  min-width: 250px;
}
</style>
