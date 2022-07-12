<template>
  <p>Reaction time: {{ score }} ms</p>
  <h2>your are: {{ rank }}</h2>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "ninja!";
    } else if (this.score < 500) {
      this.rank = "you are fast";
    } else {
      this.rank = "you are slow";
    }
  },
};
</script>

<style></style>
