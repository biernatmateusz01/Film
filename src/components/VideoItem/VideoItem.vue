<template>
  <div v-if="props.data" class="film-container">
    <video
      @timeupdate="processChange()"
      autoplay
      ref="video"
      id="video_player"
      class="video_player"
      style="width: 100%"
    >
      <source :src="film.src" type="video/mp4" />
    </video>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const currentTime = ref(0);
const video = ref(null);

const props = defineProps({
  film: Object,
  data: Boolean,
});

const debounce = (func, timeout = 1) => {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, args);
    }, timeout);
  };
};

const getMyFilmInfs = () => {
  if (props.data) {
    currentTime.value = video.value.currentTime;
    if (currentTime.value === 0) {
      console.log("początek filmu");
    } else if (video.value.ended === true) {
      console.log("koniec filmu");
    } else if (
      Number(
        video.value.currentTime.toFixed(0) * 2 ===
          Number(video.value.duration.toFixed(0))
      )
    ) {
      console.log("środek filmu");
    }
  }
};

const processChange = debounce(getMyFilmInfs);

const checkVideo = watch(
  () => props.data,
  (newCount, oldCount) => {
    if (newCount === true) {
      processChange();
    } else if (oldCount === true) {
      console.clear();
      return;
    }
  }
);
</script>

<style lang="scss">
.film-container {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 48px;
  padding: 16px 0;

  video {
    width: 100%;
    height: 100%;
    border-radius: 4px;
    box-shadow: (0px 4px 4px rgba(0, 0, 0, 0.25));
  }
}

@media (min-width: 600px) {
  .film-container {
    flex-direction: row;
    padding: 48px;
  }
}
</style>
