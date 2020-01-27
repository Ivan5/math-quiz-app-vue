<template>
  <div id="app">
    <h1>Math Quiz App</h1>
    {{ this.operator}}
    <button @click="selectOperator('+')">
      Addition
      <br />+
    </button>
    <button @click="selectOperator('-')">
      Subtraction
      <br />-
    </button>
    <button @click="selectOperator('/')">
      Division
      <br />/
    </button>
    <button @click="selectOperator('*')">
      Multiplication
      <br />*
    </button>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      operator: null
    };
  },
  methods: {
    selectOperator(operator) {
      this.operator = operator;
    }
  },
  components: {}
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}

button {
  padding: 10px;
  width: 160px;
  height: 80px;
  margin-right: 10px;
  background-color: #10aeb2;
  color: #fff;
  font-size: 20px;
  cursor: pointer;
  vertical-align: top;
}
</style>
