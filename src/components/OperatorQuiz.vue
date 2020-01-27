<template>
  <div>
    <div v-if="isQuizStarted">
      <h4>{{operandLeft}} {{operator}} {{operandRight}}</h4>

      <button
        @click="selectAnswer(answer)"
        v-for="(answer,index) of answers"
        :key="index"
      >{{answer}}</button>
    </div>

    <div v-if="!isQuizStarted">
      <button @click="startQuiz">Start</button>
    </div>

    <button @click="$emit('onBack')">Back</button>
  </div>
</template>
<script>
export default {
  props: ["operator"],
  data() {
    return {
      isQuizStarted: false,
      operandLeft: null,
      operandRight: null,
      answers: [],
      expectedAnswer: null
    };
  },
  methods: {
    selectAnswer(answerSelected) {
      if (answerSelected === this.expectedAnswer) {
        this.startQuiz();
      } else {
        alert("Wrong Answer");
      }
    },
    startQuiz() {
      this.isQuizStarted = true;
      this.operandLeft = parseInt(Math.random() * 13);
      this.operandRight = parseInt(Math.random() * 13);

      const methods = {
        "+": (a, b) => a + b,
        "-": (a, b) => a - b,
        "/": (a, b) => a / b,
        "*": (a, b) => a * b
      };

      const methodToUse = methods[this.operator];

      for (let i = 0; i < 5; i++) {
        const answer = methodToUse(
          parseInt(Math.random() * 3),
          parseInt(Math.random() * 3)
        );

        this.answers.push(answer);
      }
      const expectedAnswer = methodToUse(this.operandLeft, this.operandRight);
      this.answers[
        parseInt(Math.random() * this.answers.length)
      ] = expectedAnswer;
      this.expectedAnswer = expectedAnswer;
    }
  }
};
</script>
<style lang="">
</style>