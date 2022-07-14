<template>
  <!-- <button @click="start" :disabled="isPlaying">play</button> -->
  <!-- <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" /> -->
  <SignupForm />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
import SignupForm from "./components/SignupForm.vue";

export default {
  name: "App",
  components: { Block, Results, SignupForm },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style></style>
