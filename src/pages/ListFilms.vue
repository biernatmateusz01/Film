<template>
  <div>
    <ul class="films-container">
      <li v-for="film in films" :key="film.id">
        <FilmItem :film="film" />
      </li>
    </ul>
  </div>
</template>

<script setup>
import FilmItem from "../components/FilmItem/FilmItem.vue";
import axios from "axios";
import { ref } from "vue";
const films = ref([]);

const getMyData = () => {
  axios.get("../../../data.json").then((response) => {
    films.value = response.data.films;
  });
};

getMyData();
</script>

<style>
.films-container {
  display: flex;
  flex-direction: column;
  gap: 32px;
}
</style>
