<template>
 <div class="p-3" style="max-width: 400px; margin: 50px auto; background: #234">

  <!-- Calculator Result -->
    <div 
      class="w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-vue-dark" 
      style="direction: rtl;">
      {{ calculatorValue || 0 }}
    </div>

    <!-- calculator buttons -->
<div class="row no-gutters">
  <div class="col-3" v-for="(n) in calculaatorElemnets" :key="n">
    <div class="lead text-center text-white m-1 p-3 bg-vue-dark rounded hover-class"
      :class="{'bg-vue-green': ['C','*','/','-','+','%','='].includes(n)}"
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
  name: 'CalculatorApp',
  props: {
    msg: String
  },
  data() {
    return {
      calculatorValue: '',
      calculaatorElemnets :['C','*','/','-',7,8,9,'+',4,5,6,'%',1,2,3,'=',0,'.'],
      operator: null,
      previousCalculatorValue: ''
    }
  },
  methods: {
    action(n) {
  /* Append value */
  if(!isNaN(n) || n === '.'){
        this.calculatorValue += n + '';
      }
  /* Clear */
  if(n === 'C'){
        this.calculatorValue = '';
      }
  /* Percentage */
  if(n === '%'){
        this.calculatorValue = this.calculatorValue / 100 + '';
      }
   /* Operators */
  if(['/','*','-','+'].includes(n)){
        this.operator = n;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = '';
      }
    /* Calculate result using the eval function */
    if(n === '='){
        this.calculatorValue = eval(
          this.previousCalculatorValue + this.operator + this.calculatorValue
        );
        this.previousCalculatorValue = '';
        this.operator = null;
      }
  }
}
}
</script>

<style scoped>
.bg-vue-dark {
    background: #31475e;
}
.hover-class:hover {
    cursor: pointer;
    background: #3D5875;
  }
  .bg-vue-green {
    background: #3fb984;
  }
</style>
