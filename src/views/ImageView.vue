<script setup>
import { inject, onMounted, ref } from "vue";

const props = defineProps({
  id: String,
});

const { addToFavs } = inject("favs");

const imageDetails = ref(null);

onMounted(async () => {
  const response = await fetch(
    `https://api.unsplash.com/photos/${String(
      props.id
    )}?client_id=dhMA85RAZd4pMnpJprdOcvgMf6vMzrBH2HaV8Z4KtHM`
  );
  const res = await response.json();
  imageDetails.value = res;
});
</script>

<template>
  <div class="container">
    <div class="top_wrapper">
      <div class="author">
        <div class="avatar">
          <img :src="imageDetails?.user?.profile_image?.medium" alt="author" />
        </div>
        <div class="name">
          <p class="main">{{ imageDetails?.user?.name }}</p>
          <p class="secondary">
            @{{ imageDetails?.user?.social?.instagram_username }}
          </p>
        </div>
      </div>
      <div class="buttons">
        <div class="fav_button" @click="addToFavs(imageDetails)">
          <img src="../assets/fav_button.png" alt="fav_button" />
        </div>
        <div class="download_button">
          <img src="../assets/download_button.png" alt="download_button" />
        </div>
      </div>
    </div>
    <main class="image_wrapper">
      <img
        :src="imageDetails?.urls?.regular"
        :alt="imageDetails?.alt_description"
      />
    </main>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 15px 0;
}
.top_wrapper {
  display: flex;
  padding: 0 2rem;
  justify-content: space-between;
}

.author {
  display: flex;
  flex: 1;
}
.avatar img {
  border-radius: 5px;
}

.name .main {
  font-size: 15px;
}

.name .secondary {
  font-size: 12px;
  color: rgb(133, 130, 130);
}

.buttons {
  display: flex;
}
.image_wrapper {
  text-align: center;
  padding: 1rem;
}
.image_wrapper img {
  border-radius: 10px;
  object-fit: cover;
  width: 100%;
  max-width: 1024px;
  height: auto;
}
</style>
