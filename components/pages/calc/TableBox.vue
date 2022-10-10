<template>
  <div class="table-box">
    <div class="table-box__inner">
      <Box
        v-for="(item, index) in boxList"
        :key="`table-box__${index}`"
        :boxListData="item"
        @click="onSelectNum(item)"
      />

      <div class="table-box__btn">
        <CustomButton @click="$emit('onClear')" theme="white" size="xl"
          >Clear
        </CustomButton>
      </div>
      <div class="table-box__btn">
        <CustomButton @click="$emit('onDelete')" theme="white" size="xl"
          >Del
        </CustomButton>
      </div>
    </div>
  </div>
</template>
<script>
import Box from "@/components/Box.vue";
import CustomButton from "@/components/common/controls/CustomButton.vue";

export default {
  components: {
    Box,
    CustomButton,
  },
  props: {
    boxList: {
      type: Array,
      required: true,
    },
    resultData: {
      type: Number,
    },
  },
  data() {
    return {};
  },
  methods: {
    onSelectNum(item) {
      if (this.resultData === 0) {
        this.$emit("onChangeResult", item.name);
        return;
      }
      const newResult = Number(String(this.resultData) + String(item.name));
      this.$emit("onChangeResult", newResult);
    },
  },
};
</script>
<style lang="scss">
.table-box {
  // .table-box__inner
  &__inner {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 4px;
  }
  //   .table-box__btn
  &__btn {
    overflow: hidden;
  }
}
</style>
