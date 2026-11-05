<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h1>Click me</h1>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      startTime: null,
      reactionTime: 0,
      showBlock: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.startTime = Date.now();
    },
    stopTimer() {
      this.reactionTime = Date.now() - this.startTime;
      this.showBlock = false;
      console.log("Reaction Time:", this.reactionTime, "ms");
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border: 2px solid black;
  border-radius: 15px;
  padding: 100px 0;
  margin: 40px auto;
  background-image: linear-gradient(30deg, #e1f99e 0%, #6adfdf 100%);
}
h1 {
  font-family: "Courier New", Courier, monospace;
}
</style>
