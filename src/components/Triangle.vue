<template>
  <div>
    <div id="triangle">
      <my-row
        v-for="i in parseInt(triangleHeight)"
        :key="i"
        :row-height="i"
        :triangle-height="triangleHeight"
        :mod="remainder"
      />
    </div>
    <div id="options-list">
      <div class="option-element">
        <b><p>Height</p></b>
        <div class="slider-container">
          <input
            type="range"
            class="slider"
            name="height"
            min="2"
            max="75"
            v-model="triangleHeight"
          />
        </div>
      </div>
      <div class="option-element">
        <b><p>Remainder</p></b>
        <input
          type="number"
          name="remainder"
          min="1"
          max="9"
          minlength="1"
          maxlength="1"
          v-model="remainder"
        />
      </div>
    </div>
  </div>
</template>
<script>
import MyRow from "./Row.vue";

export default {
  name: "Triangle",
  components: {
    MyRow,
  },
  data() {
    return {
      triangleHeight: 7,
      remainder: 2,
    };
  },
  props: {},
};
</script>
<style lang="scss" scoped>
@import "../css/variables.css";
input[type="number"] {
  border: none;
  background-color: var(--color-line-list);
  color: var(--color-font);
  height: 20px;
}

#triangle {
  height: calc(var(--triangle-wh) + 50px);
  padding-top: 90px;
}

#options-list {
  margin-top: 20px;
  display: flex;
  justify-content: flex-start;
}

.option-element {
  margin-right: 80px;
}

.slider-container {
  width: 100%;
}
.slider {
  -webkit-appearance: none;
  appearance: none;
  width: 100%;
  height: 15px;
  background: var(--least-dark);
  outline: none;
  opacity: 0.7;
  -webkit-transition: 0.2s;
  transition: opacity 0.2s;
  &:hover {
    opacity: 1;
  }
  &::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 25px;
    height: 15px;
    background: var(--darker);
    cursor: pointer;
  }
  &::-moz-range-thumb {
    width: 25px;
    height: 15px;
    background: var(--darker);
    cursor: pointer;
  }
}
</style>
