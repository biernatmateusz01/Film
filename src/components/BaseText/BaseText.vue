<template>
  <p class="heading" :class="isBlack ? 'heading-black' : 'heading-gray'">
    <slot></slot>
  </p>
</template>

<script setup>
defineProps({
  isBlack: Boolean,
});
</script>

<style lang="scss">
$black: #000000;
$gray: #6b7280;

.heading {
  font-weight: 500;
  font-size: 12px;
  line-height: 15px;
}
.heading-black {
  color: $black;
}
.heading-gray {
  color: $gray;
}
</style>
