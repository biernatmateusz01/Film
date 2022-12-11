<template>
  <div>
    <div class="wrapper">
      <div class="info-container">
        <div class="img-container">
          <img :src="film.img" alt="" />
        </div>
        <div class="text-container">
          <div class="text-container__top">
            <BaseText>{{ film.year }}</BaseText>
            <BaseText isBlack>{{ film.time }}</BaseText>
          </div>
          <div class="text-container__center">
            <BaseTitle>{{ film.name }}</BaseTitle>
            <BaseText>{{ film.category }}</BaseText>
          </div>
          <div class="text-container__bottom">
            <BaseText>{{ film.text }}</BaseText>
          </div>
          <div class="button-container">
            <BaseButton v-if="!isOpen" @click="isOpen = !isOpen"
              >expand_more
            </BaseButton>
            <BaseButton v-else @click="isOpen = !isOpen"
              >expand_less
            </BaseButton>
          </div>
        </div>
      </div>
      <VideoItem
        :key="film.id"
        :film="film"
        :data="isOpen"
      />
    </div>
  </div>
</template>

<script setup>
import BaseText from "../BaseText/BaseText.vue";
import BaseButton from "../BaseButton/BaseButton.vue";
import VideoItem from "../VideoItem/VideoItem.vue";
import BaseTitle from "../BaseTitle/BaseTitle.vue";
import { ref } from "vue";

const isOpen = ref(false);

defineProps({
  film: Object,
});
</script>

<style lang="scss">
$black: #000000;
.wrapper {
  display: flex;
  flex-direction: column;
  background: white;
  padding: 16px;
  color: $black;
  width: 100%;
  transition: transform 0.4s;
  border-radius: 4px;
  padding: 32px;

  .info-container {
    display: flex;
    flex-direction: column;
    gap: 32px;
    justify-content: space-between;
    height: 100%;
  }

  .img-container {
    overflow: hidden;
    box-shadow: (0px 4px 4px rgba(0, 0, 0, 0.25));
    border-radius: 4px;
    height: 350px;
    overflow: hidden;

    img {
      height: 100%;
      width: 100%;
      object-fit: cover;
      transition: transform 0.8s;

      &:hover {
        transform: scale(1.1);
      }
    }
  }

  .text-container {
    display: flex;
    flex-direction: column;
    flex: 1;

    .text-container__top {
      display: flex;
      justify-content: space-between;
      margin-bottom: 4px;
    }

    .text-container__center {
      display: flex;
      flex-direction: column;
      gap: 8px;
      margin-bottom: 24px;
    }
  }

  .button-container {
    display: flex;
    justify-content: end;
    transition: transform 0.4s;
    margin-top: 12px;
  }
}

@media (min-width: 600px) {
  .wrapper {
    .info-container {
      flex-direction: row;
    }

    .img-container {
      width: 126px;
      height: 187px;
    }
  }
}

@media (min-width: 1000px) {
  .wrapper {
    .text-container__bottom {
      width: 440px;
    }
  }
}
</style>
