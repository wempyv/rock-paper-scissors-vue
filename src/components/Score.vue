<template>
  <section class="section-score">
    <div class="row justify-content-between">
      <div class="col title-score">
        <span>ROCK</span><br />
        <span>PAPER</span><br />
        <span>SCISSORS</span>
      </div>
      <div class="col score-results">
        <div class="score-result ml-auto text-center">
          <span>SCORE</span>
          <h1>{{ userScore }}</h1>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["userScore"],
};
</script>

<style></style>
