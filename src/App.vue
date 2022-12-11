<template>
  <main>
    <div class="wrapper-app">
      <ListFilms />
    </div>
  </main>
</template>

<script setup>
import ListFilms from "../src/pages/ListFilms.vue";
</script>

<style lang="scss">
.wrapper-app {
  max-width: 1800px;
  display: block;
  margin: auto;
}
</style>
