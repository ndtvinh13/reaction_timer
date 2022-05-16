<template>
  <h1>⏲ My Reaction Timer</h1>
  <button @click="start" class="start" :disabled="isPlaying">
    Click to play 🎉
  </button>
  <Result v-if="showResult" :result="score"></Result>
  <div v-if="isPlaying">
    <Block :delay="delay" @end="endGame" />
  </div>
</template>

<script>
// imports
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
      showResult: false,
    };
  },

  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
      this.showResult = false;
    },

    // Pass with a value
    endGame(reacionTime) {
      this.score = reacionTime;
      this.isPlaying = false;
      this.showResult = true;
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

.start {
  color: #42b883;
  padding: 15px 30px;
  margin-bottom: 20px;
  background-color: #fff;
  border: rgb(206, 205, 205) solid 1px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 20px;
  font-weight: 500;
  transition: 0.3s;
}

.start:hover {
  border: rgb(175, 175, 175) solid 1px;
  background-color: rgb(241, 241, 241);
}

.start:disabled {
  background-color: rgb(226, 226, 226);
  border: rgb(226, 226, 226) 1px solid;
  color: rgb(182, 182, 182);
}
</style>
