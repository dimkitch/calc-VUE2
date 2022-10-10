<template>
  <aside class="table-box-aside">
    <Box
      class="table-box-aside__item"
      :boxListData="{ id: 1, name: '+' }"
      theme="grey"
      @click="$emit('onSetMathOperation', '+')"
    />
    <Box
      class="table-box-aside__item"
      :boxListData="{ id: 2, name: '-' }"
      theme="grey"
      @click="$emit('onSetMathOperation', '-')"
    />
    <Box
      class="table-box-aside__item"
      :boxListData="{ id: 3, name: '/' }"
      theme="grey"
      @click="$emit('onSetMathOperation', '/')"
    />
    <Box
      class="table-box-aside__item"
      :boxListData="{ id: 4, name: '*' }"
      theme="grey"
      @click="$emit('onSetMathOperation', '*')"
    />
    <Box
      class="table-box-aside__item"
      :boxListData="{ id: 5, name: '=' }"
      theme="grey"
      @click="$emit('onSetMathOperation', '=')"
    />
  </aside>
</template>
<script>
import Box from "@/components/Box.vue";
export default {
  props: {},
  components: {
    Box,
  },
};
</script>
<style lang="scss">
.table-box-aside {
  display: grid;
  grid-template-columns: 1fr;
  gap: 4px;
}
</style>
