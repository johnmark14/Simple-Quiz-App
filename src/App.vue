<template>
  <div class="ctr">
    <questions
      v-if="questionsAnswered < questionsData.length"
      :questionsData="questionsData"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    />
    <results v-else :results="results" :totalCorrect="totalCorrect" />
    <button type="button" class="reset-btn">Reset</button>
  </div>
</template>

<script>
import Questions from "./components/questions.vue";
import Results from "./components/results.vue";

export default {
  name: "App",
  components: {
    Questions,
    Results,
  },
  methods: {
    questionAnswered(answer) {
      this.totalCorrect = answer ? this.totalCorrect++ : this.totalCorrect;

      // Increment questionsAnswered data
      this.questionsAnswered++;
    },
  },
  data() {
    return {
      totalCorrect: 0,
      questionsAnswered: 0,
      questionsData: [
        {
          q: "What is 2 + 2?",
          answers: [
            {
              text: "4",
              is_correct: true,
            },
            {
              text: "3",
              is_correct: false,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: "5",
              is_correct: false,
            },
          ],
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: "5",
              is_correct: false,
            },
            {
              text: "7",
              is_correct: false,
            },
            {
              text: "6",
              is_correct: true,
            },
            {
              text: "12",
              is_correct: false,
            },
          ],
        },
        {
          q: "Find the missing letter: C_ke",
          answers: [
            {
              text: "e",
              is_correct: false,
            },
            {
              text: "a",
              is_correct: true,
            },
            {
              text: "i",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
};
</script>

