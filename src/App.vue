<script>
export default {
  data() {
    return {
      number1: 0,
      number2: 0,
      selectedOperator: 'somar',
      result: 0,
    };
  },
  methods: {
    calculate() {
      const operations = {
        somar: (a, b) => a + b,
        subtrair: (a, b) => a - b,
        multiplicar: (a, b) => a * b,
        dividir: (a, b) => (b !== 0 ? a / b : 'Infinity'),
      };

      const operation = operations[this.selectedOperator];
      this.result = operation(parseFloat(this.number1), parseFloat(this.number2));
    },
  },
};
</script>

<template>
    <div>
      <input v-model="number1" @change="calculate" type="number" />
      <select v-model="selectedOperator" @change="calculate">
        <option value="somar">+</option>
        <option value="subtrair">-</option>
        <option value="multiplicar">*</option>
        <option value="dividir">/</option>
      </select>
      <input v-model="number2" @change="calculate" type="number" />
      <p>Resultado: {{ result }}</p>
  </div>
</template>

<style scoped>
</style>
