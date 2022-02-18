<template>
  <div class="row" :style="style">
    <my-circle
      v-for="i in rowHeight"
      :key="i"
      :value="rowHeight"
      :width="triangleHeight"
      :column="i"
      :mod="mod"
    ></my-circle>
  </div>
</template>
<script>
import MyCircle from "./Circle.vue";
export default {
  name: "Row",
  components: {
    MyCircle,
  },
  props: {
    rowHeight: Number,
    triangleHeight: Number,
    mod: Number,
  },
  computed: {
    style() {
      return (
        "height: calc(var(--triangle-wh) / " +
        this.triangleHeight +
        " - (var(--triangle-wh) /" +
        this.triangleHeight +
        " * 0.1)) !important;"
      );
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../css/variables.css";
.row {
  width: var(--triangle-wh);
  display: flex;
  justify-content: center;
}
</style>
