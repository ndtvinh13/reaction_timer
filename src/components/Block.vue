<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],

  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },

  //Vue hook lifecyle
  // mounted  state
  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  // updated state
  updated() {
    console.log("component updated");
  },

  // unmounted state
  unmounted() {
    console.log("unmounted");
  },

  //method
  methods: {
    startTimer() {
      // use to store timer time in  data()
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    stopTimer() {
      // stop the interval
      clearInterval(this.timer);
      console.log(this.reactionTime);
      // event name then data
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 30%;
  border-radius: 10px;
  background-color: #42b883;
  color: #fff;
  text-align: center;
  padding: 8%;
  font-size: 45px;
  margin: auto;
  cursor: pointer;
}
</style>
