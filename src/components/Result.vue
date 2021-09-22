<template>
  <div class="score">
    Your Reaction Time is {{ score }} Ms
    <p>Rank : {{ rank }}</p>
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
      this.rank = "Ninja Fingers";
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = " Snail Pace...";
    }
  },
};
</script>
<style>
.score {
  background: #156594;
  width: 400px;
  color: white;
  text-align: center;
  padding: 1rem 0;
  margin: 1rem auto;
  border-radius: 4px;
}
</style>
