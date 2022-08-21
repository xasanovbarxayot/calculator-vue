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
<div class="col-3"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalCulator",
  data() {
    return {
      calculatorValue: "",
      calculatorElements:["C", "*","/","-",7,8,9,"+",4,5,6,"%",1,2,3,"=",0,"."]
    };
  },
};
</script>

<style scoped>
.bg-vue-dark {
  text-align: right;
  background-color: #31475e;
}
</style>
