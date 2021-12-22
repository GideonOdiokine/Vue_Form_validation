<template>
  <h3>This is your Time Reaction: {{ score }}</h3>
  <p>Rank:: {{ rank }}</p>
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
      this.rank = "Gidi Fingers";
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = " Snail pace";
    }
  },
};
</script>

<style></style>
