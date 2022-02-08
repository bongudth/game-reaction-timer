<template>
  <div class="results">Reaction time: {{ score }}ms</div>
  <h2>{{ rank }}</h2>
</template>

<script>
export default {
  name: 'Results',
  props: ['score'],
  data() {
    return {
      rank: null,
    }
  },
  mounted() {
    if(this.score < 250) {
      this.rank = 'Ninja Fingers!';
    } else if(this.score < 400) {
      this.rank = 'Rapid Reaction!';
    } else {
      this.rank = 'Slowpoke!';
    }
  },
}
</script>

<style>
  h2 {
    color: rgb(34, 187, 93);
  }
</style>
