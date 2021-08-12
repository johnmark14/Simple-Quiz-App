<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{
          width: `${(questionsAnswered / questionsData.length) * 100}%`,
        }"
      ></div>
      <div class="status">
        {{ questionsAnswered }} out of {{ questionsData.length }} questions
        answered
      </div>
    </div>
    <transition-group name="fade">
      <div
        class="single-question"
        v-for="(questions, index) in questionsData"
        :key="questions.q"
        v-show="questionsAnswered === index"
      >
        <div class="question">{{ questions.q }}</div>
        <div class="answers">
          <div
            class="answer"
            v-for="answer in questions.answers"
            v-bind:key="answer.text"
            @click.prevent="selectAnswer(answer.is_correct)"
          >
            {{ answer.text }}
          </div>
        </div>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: ["questionsData", "questionsAnswered"],
  emits: ["question-answered"],
  methods: {
    selectAnswer(isCorrect) {
      this.$emit("question-answered", isCorrect);
    },
  },
};
</script>

<style>
</style>