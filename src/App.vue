<template>
  <div id="app">
    <h1>Math Quiz App</h1>
    <OperatorQuizVue @onBack="clearOperator" v-if="operator" :operator="operator" />
    <OperatorSelectorVue v-if="!operator" @changeOperator="changeOperator" />
  </div>
</template>

<script>
import OperatorSelectorVue from "./components/OperatorSelector.vue";
import OperatorQuizVue from "./components/OperatorQuiz.vue";

export default {
  name: "app",
  data() {
    return {
      operator: null
    };
  },
  methods: {
    changeOperator(operator) {
      this.operator = operator;
    },
    clearOperator() {
      this.operator = null;
    }
  },
  components: {
    OperatorSelectorVue,
    OperatorQuizVue
  }
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
