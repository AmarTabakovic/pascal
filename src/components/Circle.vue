<template>
  <div class="circle" :style="style"></div>
</template>
<script>
export default {
  name: "Circle",
  data() {
    return {};
  },
  props: {
    value: Number,
    width: Number,
    column: Number,
    mod: Number,
  },
  methods: {
    getColorForCircle(n, k) {
      const binomial = Math.round(this.calculateBinomialCoefficient(n, k));
      const remainder = binomial % this.mod;
      switch (remainder) {
        case 0:
          return "#bf616a";
        case 1:
          return "#3b4252";
        case 2:
          return "#a3be8c";
        case 3:
          return "#5e81ac";
        case 4:
          return "#824147";
        case 5:
          return "#59684d";
        case 6:
          return "#5e81ac";
        case 7:
          return "#ebcb8b";
        case 8:
          return "#b48ead";
        case 9:
          return "#8fbcbb";
        default:
          return "#3b4252";
      }
    },
    calculateBinomialCoefficient(n, k) {
      return this.factorial(n) / (this.factorial(k) * this.factorial(n - k));
    },
    factorial(num) {
      var v = 1;
      for (var i = 2; i <= num; i++) v = v * i;
      return v;
    },
  },
  computed: {
    style() {
      return (
        "width: calc(var(--triangle-wh) / " +
        this.width +
        "); height: calc(var(--triangle-wh) / " +
        this.width +
        ");  border-radius: calc(var(--triangle-wh) / " +
        this.width +
        " / 2); background-color: " +
        this.getColorForCircle(this.value - 1, this.column - 1) +
        ";"
      );
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../css/variables.css";
</style>
