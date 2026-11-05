<template>
  <div class="card">
    <h2>Reaction Time: {{ score }} ms</h2>
    <p class="rank">Rank:{{ rank }}</p>
  </div>
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
    if (this.score < 200) {
      this.rank = "Pro";
    } else if (this.score < 400) {
      this.rank = "good";
    } else {
      this.rank = "Snail pace";
    }
    console.log(this.rank);
  },
};
</script>

<style scoped>
.rank {
  font-family: "Courier New", Courier, monospace;
  width: 150px;
  padding: 20px 0;
  border-radius: 5px;
  border: 1px solid black;
  margin: 0 auto;
  margin-top: 20px;
}
.card {
  width: 250px;
  background-color: #ffffff;
  border-radius: 12px;
  border: 1px solid black;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  margin: 40px auto;
  padding: 100px 0;
  background-image: linear-gradient(135deg, #fbbbdb 0%, #fcfdab 100%);
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.2);
}
h2 {
  font-family: "Courier New", Courier, monospace;
}
</style>
