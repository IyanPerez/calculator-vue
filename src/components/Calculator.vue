<!-- header side -->
<template>
  <!-- header side -->
  <header>
    
    
    <div class="p-5 text-center bg-light">
      <h1 class="mb-3">Calculator</h1>
     
      
      
    </div>
    
  </header>


    <!-- Happy Coding -->
    <div class= "p-3" style= "max-width: 400px; margin: 50px auto; background: #234">
      
      <!-- Calculator Result -->
      <div class= "w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-vue-dark">
        {{ calculatorValue || 0 }}
      </div>
  
      <!-- Calculator buttons -->
      <div class= "row no-gutters">
        <div class= "col-3" v-for="n in calculatorElements" :key="n">
          <div class= "lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
            :class= "{'bg-vue-green': ['C','*','/','-','+','%','='].includes(n)}"
            @click="action(n)">
            {{ n }}
           
          </div>
        </div>
       
      </div>
       <!-- button for chaning money -->
      <input label="Eur" type="number" />
      <h6 style="background-color: white">rue </h6>
      <input label="Number input" type="number" />
      <input label="Number input" type="number" />
      <input label="Number input" type="number" />
    </div>
    
    <!-- footer side  -->
    <MDBFooter :text="['center', 'lg-start']">
    <!-- Copyright -->
    <div class="text-center p-3" style="background-color: white">
      © 2022 Copyright: Iyan  Y omid
      
    </div>
    <!-- Copyright -->
  </MDBFooter>
  
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
      action(n){
  
        /* Append value */
        if(!isNaN(n) || n === '.'){
          this.calculatorValue += n + '';
        }
  
        /* Clear value */
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
      background: #51315e;
    }
    .hover-class:hover {
      cursor: pointer;
      background: #3d7175;
    }
    .bg-vue-green {
      background: #0b5535;
    }
    
  </style>
  