<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start" class="btn" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showScore" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false,
    };
  },
  methods: {
    start() {
      this.showScore = false;
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
    },
    endGame(reactionTime) {
      this.showScore = true;
      this.score = reactionTime;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn {
  background: #1871a5;
  border: 0;
  color: aliceblue;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
}
.btn:disabled {
  background: #5c91af;
  cursor: not-allowed;
}
</style>
