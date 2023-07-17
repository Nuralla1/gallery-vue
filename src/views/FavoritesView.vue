<script setup>
import { inject } from "vue";

const { favs, removeFromFavs } = inject("favs");
</script>

<template>
  <div class="container">
    <div
      v-for="fav in favs"
      :key="fav?.id"
      class="img_wrapper"
      @click="removeFromFavs(fav)"
    >
      <img :src="fav?.urls?.regular" />
    </div>
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
}

.img_wrapper img {
  border-radius: 10px;
  object-fit: cover;
  width: 300px;
  height: 300px;
}

@media (min-width: 480px) {
  .container {
    max-width: 1054px;
    flex-direction: row;
    flex-wrap: wrap;
    align-self: center;
    margin: 20px auto;
  }
}
</style>
