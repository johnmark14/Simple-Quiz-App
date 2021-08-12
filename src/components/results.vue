<template>
  <div class="result">
    <div class="title">{{ results[resultsIndex].title }}</div>
    <div class="desc">{{ results[resultsIndex].desc }}</div>
  </div>
</template>

<script>
export default {
  props: ["results", "totalCorrect"],
  computed: {
    resultsIndex() {
      let index = 0;

      this.results.forEach((element, i) => {
        if (
          element.min <= this.totalCorrect &&
          element.max >= this.totalCorrect
        ) {
          index = i;
        }
      });
      //console.log(this.results[index].title);
      return index;
    },
  },
};
</script>

<style>
</style>