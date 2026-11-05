<template>
  <h1>Ninja Reaction Timer</h1>

  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",

  components: {
    Block,
    Result,
  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;

      console.log(this.delay);
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.showResult = true;
      this.isPlaying = false;
    },
  },
};
</script>
<style scoped>
button {
  width: 150px;
  border: 2px solid black;
  border-radius: 10px;
  font-family: "Courier New", Courier, monospace;
  padding: 20px;
  margin: 0 auto;
  background-image: linear-gradient(135deg, #8ce4b5 0%, #64f1f1 100%);
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
}

button:hover {
  cursor: pointer;
}
</style>
