<template>
  <button
    class="custom-button"
    @click="$emit('click')"
    :class="`custom-button--${size} custom-button--${theme}`"
  >
    <slot></slot>
  </button>
</template>
<script>
export default {
  props: {
    theme: {
      type: String,
    },
    size: {
      type: String,
    },
  },
};
</script>
<style lang="scss">
.custom-button {
  cursor: pointer;
  transition: $transition-mod;
  overflow: hidden;

  // .custom-btn--xl
  &--xl {
    width: 100%;
    height: 100%;
  }
  // .custom-btn--xl
  &--xm {
    width: 100%;
    height: 100%;
    border-radius: 30px;
    padding: 15px 20px;
  }
  // .custom-btn--white
  &--white {
    background-color: white;
    //   .custom-button--white:hover
    &:hover {
      background-color: rgb(0, 0, 0);
      color: rgb(255, 255, 255);
      scale: 1.2;
    }
  }
  // .custom-btn--primary
  &--primary {
    color: rgb(255, 255, 255);
    background-color: rgb(50, 75, 186);
    //   .custom-button--white:hover
    &:hover {
      background-color: rgb(18, 53, 210);
      color: rgb(255, 255, 255);
      scale: 1.2;
    }
  }
}
</style>
