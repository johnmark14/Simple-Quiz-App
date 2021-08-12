<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar"></div>
      <div class="status">1 out of 3 questions answered</div>
    </div>
    <div
      class="single-question"
      v-for="questions in questionsData"
      :key="questions.q"
    >
      <div class="question">{{ questions.q }}</div>
      <div class="answers">
        <div
          class="answer"
          v-for="answer in questions.answers"
          v-bind:key="answer.text"
        >
          {{ answer.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["questionsData"],
};
</script>

<style>
</style>