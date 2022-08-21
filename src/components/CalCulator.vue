<template>
  <div
    class="p-3"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <div
      class="w-full rounded m-1 p-3 lead font-weight-bold text-white bg-vue-dark"
    >
      {{ calculatorValue || 0 }}
    </div>
    <div class="row no-gutters">
      <div class="col-3" v-for="n in calculatorElements" :key="n">
        <div
          class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
          :class="{
            'bg-vue-green': ['C', '*', '/', '-', '+', '%', '=', ''].includes(n),
          }"
          @click="action(n)"
        >
          {{ n }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalCulator",
  data() {
    return {
      calculatorValue: "",
      calculatorElements: [
        "C",
        "*",
        "/",
        "-",
        7,
        8,
        9,
        "+",
        4,
        5,
        6,
        "%",
        1,
        2,
        3,
        "=",
        0,
        ".",
      ],
      operator: null,
      previouscalculatorValue: "",
    };
  },
  methods: {
    action(n) {
      if (!isNaN(n) || n === ".") {
        this.calculatorValue += n + "";
      }
      if (n === "C") {
        this.calculatorValue = "";
      }
      if (n === "%") {

        this.calculatorValue = this.calculatorValue / 100 + "";
      }
      if (["/", "*", '-', '+'].includes(n)) {
        this.operator = n;
        this.previouscalculatorValue = this.calculatorValue;
        this.calculatorValue=""
      }
      if (n === '=') {
        this.calculatorValue = eval(
          this.previouscalculatorValue + this.operator + this.calculatorValue
        );
        this.operator = null;
        this.previouscalculatorValue = "";
      }
    },
  },
};
</script>

<style >
.bg-vue-dark {
  text-align: right;
  background-color: #31475e;
}
.bg-vue-green {
  background-color: #3fb984;
}
.hover-class:hover {
  cursor: pointer;
  background-color: #3d5875;
}
</style>
