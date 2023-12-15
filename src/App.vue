<script setup>
  import { reactive } from 'vue';
  const calculator = reactive({
    result: 0,
    input1: 0,
    input2: 0,
    operation: 'sum',
    errorMessage: '',
  });
  function calculate() {
    switch (calculator.operation) {
      case 'sum':
        calculator.result = calculator.input1 + calculator.input2;
        break;
      case 'substract':
        calculator.result = calculator.input1 - calculator.input2;
        break;
      case 'multiply':
        calculator.result = calculator.input1 * calculator.input2;
        break;
      case 'divide':
        calculator.result = calculator.input1 / calculator.input2;
        break;
    }
  }
</script>
<template>
  <main id="calculator" class="main">
    <h1>Arithmetic Calculator</h1>
    <label for="number1">Enter the first number:</label>
    <input id="number1" class="inputs" type="number" v-model="calculator.input1" placeholder="Enter the first number" @input="calculate">
    <label for="operation">Operation:</label>
    <select id="operation" class="select" v-model="calculator.operation" @change="calculate">
      <option value="sum">+</option>
      <option value="substract">-</option>
      <option value="multiply">*</option>
      <option value="divide">/</option>
    </select>
    <label for="number2">Enter the second number:</label>
    <input id="number2" class="inputs" type="number" v-model="calculator.input2" placeholder="Enter the second number" @input="calculate">
    <h3><strong>Result</strong></h3>
    <p><strong>{{ calculator.result }}</strong></p>
  </main>
</template>
<style scoped>
  .main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .inputs {
    margin: 10px 0;
    padding: 10px;
    border-radius: 8px;
  }
  .select {
    margin: 10px 0;
    padding: 5px;
    border-radius: 8px;
  }
  .error-message {
    color: red;
  }
</style>