<template>
  <div class="box">
    <div
      class="box__item"
      :class="`box__item--${theme}`"
      @click="$emit('click')"
    >
      {{ boxListData.name }}
    </div>
  </div>
</template>
<script>
export default {
  props: {
    boxListData: {
      type: Object,
      required: true,
    },
    theme: {
      type: String,
      default: "white",
    },
  },
};
</script>
<style lang="scss">
.box {
  // .box__item
  &__item {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px;
    width: 100%;
    height: 100%;
    cursor: pointer;
    transition: $transition-mod;
    // .box__item:hover
    &:hover {
      color: rgb(255, 255, 255);
    }

    // .box__item--white
    &--white {
      background-color: white;
      &:hover {
        background-color: rgb(0, 0, 0);
      }
    }

    // .box__item--grey
    &--grey {
      background-color: rgb(206, 202, 202);
      &:hover {
        background-color: rgb(0, 0, 0);
      }
    }
  }
}
</style>
