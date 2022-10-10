<template>
  <main class="home-page">
    <div class="container">
      <div class="home-page__calc">
        <Calc />
      </div>
    </div>
  </main>
</template>

<script>
import CustomButton from "@/components/common/controls/CustomButton.vue";
import Calc from "@/components/pages/calc/index.vue";
export default {
  components: {
    CustomButton,
    Calc,
  },
};
</script>
<style lang="scss">
.home-page {
  margin-top: 144px;
  // .home-page__calc
  &__calc {
    display: flex;
    justify-content: center;
  }
}
</style>
