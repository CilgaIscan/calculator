<template>
  <div>
    <span>
      <input type="number" v-model.number="number1" @change="onChange" />
    </span>
    <span>
      <select v-model="chosenOperation" @change="onChange">
        <option
          :value="operation"
          :key="operation"
          v-for="operation in operations"
        >
          {{ operation }}
        </option>
      </select>
    </span>
    <span>
      <input type="number" v-model.number="number2" @change="onChange" />
    </span>
    <span> = </span>
    <span>
      {{ result }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
      return {
        number1: 3,
        number2: 7,
        operations: ["+", "-", "*", "/"],
        chosenOperation: "+",
        result: null,
      };
  },
  methods: {
    onChange() {
      switch (this.chosenOperation) {
        case "+":
          this.result = this.number1 + this.number2;
          break;
        case "-":
          this.result = this.number1 - this.number2;
          break;
        case "*":
          this.result = this.number1 * this.number2;
          break;
        case "/":
          this.result = (this.number1 / this.number2).toFixed(2);
          break;
        default:
          console.log("Operation is not found!");
      }
    },
  },
};
</script>

<style>
input[type="number"] {
  width: 30px;
  height: 20px;
}
</style>
