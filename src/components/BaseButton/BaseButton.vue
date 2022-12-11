<template>
  <button type="button" class="circle-button">
    <span class="material-symbols-outlined"> <slot></slot> </span>
  </button>
</template>

<style lang="scss">
$green: #1b801f;
$green_dark: #004203;
$white: #ffffff;

.circle-button {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 24px;
  width: 24px;
  border-radius: 50%;
  background: $green;
  border: none;
  cursor: pointer;

  &:hover {
    transform: scale(1.1);
    background: $green_dark;
  }

  .material-symbols-outlined {
    color: $white;
  }
}
</style>
