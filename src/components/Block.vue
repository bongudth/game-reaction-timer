<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  name: 'Block',
  props: ['delayTime'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delayTime)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit('end', this.reactionTime);
    },
  },
}
</script>

<style>
  .block {
    background-color: rgb(34, 187, 93);
    color: aliceblue;
    width: 300px;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
    cursor: pointer;
  }
</style>
