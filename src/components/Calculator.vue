<template>
  <!-- Happy Coding -->
  <div class="calculator">
    
    <!-- Calculator Result -->
    <div class="display">
      {{ calculatorValue || 0 }}
    </div>

    <!-- Calculator buttons -->
    <div class="panel">
      <div class="columns" v-for="(number, index) in calculatorElements" :key="index">
        <div class="btns"
          :class="{'actions': ['C','*','/','-','+','%','='].includes(number)}"
          @click="action(number)"
        >
          {{number}}
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Calculator',
  props: {
    msg: String
  },
  data() {
    return {
      calculatorValue: '',
      calculatorElements: ['C','*','/','-',7,8,9,'+',4,5,6,'%',1,2,3,'=',0,'.'],
      operator: null,
      previousCalculatorValue: '',
    }
  },
  methods: {
    action(number){
      /* Append value */
      if(!isNaN(number) || number === '.'){
        this.calculatorValue += number + '';
      }
      /* Clear value */
      if(number === 'C'){
        this.calculatorValue = '';
      }
      /* Percentage */
      if(number === '%'){
        this.calculatorValue = this.calculatorValue / 100 + '';
      }
      /* Operators */
      if(['/','*','-','+'].includes(number)){
        this.operator = number;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = '';
      }
      /* Calculate result using the eval function */
      if(number === '='){
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


<style>
.calculator {
  width: 400px; 
  background-color: rgba(34,36,38,.15);
  border-radius: 12px;
  margin: 50px auto; 
  padding: 10px;
}

.display {
  background-color: #F9AB0070;
  font-weight: 700;
  text-align: right;
  padding: 15px;
  margin: 5px;
  font-size: 1.2rem;
  border-radius: 6px;
}

.panel {
  display: flex;
  flex-wrap: wrap;
  margin: 0;
}

.columns{
  width: 25%;
}

.btns {
  width: 80px;
  height: 35px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  text-align: center;
  padding: 10px 0;
  margin: 5px;
  border-radius: 6px;
  font-size: 1.2rem;
  cursor: pointer;
  background-color: #31475e;
}

.actions {
  background: linear-gradient(270deg, #E3740070 0%, #F9AB0070 100%);
  color: #1B1B1B;
}

</style>
