<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header>
    <div class="container">
      <div class="logo">
        <img src="../assets/logo.png" alt="logo" />
      </div>
      <nav>
        <RouterLink to="/">
          <img src="../assets/search_icon_white.png" alt="search-icon" />
          <label class="search">Поиск</label>
        </RouterLink>
        <RouterLink to="/favorites">
          <img src="../assets/like_icon.png" alt="like-icon" />
          <label class="favorites">Избранное</label>
        </RouterLink>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem;
}

header {
  background-color: rgb(0, 0, 0);
}

.logo {
  min-width: 100px;
}

a {
  color: rgb(255, 255, 255);
  text-decoration: none;
  padding: 0 5px;
}
/* .router-link-active,
.router-link-exact-active {
  color: rgb(255, 255, 255);
  text-decoration: none;
} */
.favorites,
.search {
  padding-left: 0.5rem;
}

@media (max-width: 480px) {
  .favorites,
  .search {
    display: none;
  }
}
</style>
