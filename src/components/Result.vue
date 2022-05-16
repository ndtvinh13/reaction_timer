<template>
  <div class="result">🏆 Reaction time: {{ result }} ms ✅</div>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["result"],

  data() {
    return {
      rank: null,
    };
  },

  mounted() {
    if (this.result < 250) {
      this.rank = "You're fast !!! ⚡";
    } else if (this.result < 400) {
      this.rank = "Rapid Reflexes! 👀";
    } else {
      this.rank = "Slow poke... 🐢";
    }
  },
};
</script>

<style>
.result {
  font-size: 20px;
  font-weight: 600;
  margin: 30px;
}

.rank {
  font-size: 19px;
  font-weight: normal;
  margin: 20px;
  color: #42b883;
  font-weight: 600;
}
</style>
