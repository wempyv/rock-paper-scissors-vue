<template>
  <div class="section-final text-center mt-5">
    <h1>{{ results }}</h1>
    <button @click="playAgain" class="btn btn-light">PLAY AGAIN</button>
  </div>
</template>

<script>
export default {
  props: { results: String },
  methods: {
    playAgain() {
      this.$emit("playAgain");
    },
  },
};
</script>

<style></style>
