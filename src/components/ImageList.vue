<script setup>
import { inject, onMounted } from "vue";
import { RouterLink } from "vue-router";

const { imgs, updateImgs } = inject("gallery");

onMounted(async () => {
  const response = await fetch(
    `https://api.unsplash.com/photos?client_id=dhMA85RAZd4pMnpJprdOcvgMf6vMzrBH2HaV8Z4KtHM&per_page=9`
  );
  const res = await response.json();
  updateImgs(res);
});
</script>

<template>
  <div class="container">
    <div v-for="img in imgs" :key="img?.id" class="img_wrapper">
      <RouterLink :to="{ name: 'image', params: { id: img?.id } }">
        <img :src="img?.urls?.regular" />
      </RouterLink>
    </div>
  </div>
  <div class="loader">
    <img src="../assets/loader.png" />
  </div>
  <div class="scroll_to_top">
    <img src="../assets/scroll_to_top.png" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 15px;
  margin: 20px 0;
  position: relative;
}

.img_wrapper img {
  border-radius: 10px;
  object-fit: cover;
  width: 300px;
  height: 300px;
}

.loader {
  max-width: 20px;
  margin: 20px auto;
}
.scroll_to_top {
  display: none;
}
.scroll_to_top img {
  display: none;
  width: 40px;
}

@media (min-width: 480px) {
  .container {
    max-width: 1054px;
    flex-direction: row;
    flex-wrap: wrap;
    align-self: center;
    margin: 20px auto;
  }
  .scroll_to_top {
    position: absolute;
    right: 80px;
    bottom: -200px;
    display: block;
  }

  .scroll_to_top img {
    display: block;
  }
}
</style>
