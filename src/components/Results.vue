<template>
  <section class="section-results mt-3">
    <div class="row">
      <div class="col">
        <div class="row justify-content-center">
          <button class="m-3 icon icon-paper" :class="winner ? 'winner' : ''">
            <img :src="require(`@/assets/images/icon-${userPicked}.svg`)" alt="" />
          </button>
          <button class="m-3 icon icon-scissors">
            <img :src="require(`@/assets/images/icon-${housePicked}.svg`)" alt="" />
          </button>
        </div>
        <br />
        <div class="row justify-content-between result">
          <span class="you-picked ml-4">YOU PICKED</span>
          <span class="the-house-picked">THE HOUSE PICKED</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    userPicked: String,
    housePicked: String,
    results: String,
  },
  data() {
    return {
      winner: false,
    };
  },
  mounted() {
    if (this.results === "YOU WIN") {
      this.winner = true;
    }
  },
};
</script>

<style></style>
