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
      //const binomial = Math.round(this.calculateBinomialCoefficient(n, k));
      const binomial = this.calculateBinomialCoefficient(n, k);
      const modulo = BigInt(this.mod);
      const remainder = binomial % modulo;
      switch (remainder) {
        case 0n:
          return "#bf616a";
        case 1n:
          return "#3b4252";
        case 2n:
          return "#a3be8c";
        case 3n:
          return "#5e81ac";
        case 4n:
          return "#824147";
        case 5n:
          return "#59684d";
        case 6n:
          return "#5e81ac";
        case 7n:
          return "#ebcb8b";
        case 8n:
          return "#b48ead";
        case 9n:
          return "#8fbcbb";
        default:
          return "#3b4252";
      }
    },
    calculateBinomialCoefficient(n, k) {
      return this.factorial(n) / (this.factorial(k) * this.factorial(n - k));
    },
    factorial(num) {
      let v = 1n;
      for (let i = 2n; i <= num; i++) v = v * i;
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
