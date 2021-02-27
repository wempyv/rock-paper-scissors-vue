<template>
  <div class="container d-flex flex-column">
    <score :userScore="score"></score>
    <user-picked v-if="!isResults" @userPicked="gameStart"></user-picked>
    <div v-if="isResults">
      <results
        :userPicked="userPicked"
        :housePicked="housePicked"
        :results="results"
      ></results>
      <btn-play-again :results="results" @playAgain="gameRestart"></btn-play-again>
    </div>
    <Footer v-show="!isResults"></Footer>
  </div>
</template>

<script>
import Score from "@/components/Score.vue";
import Results from "@/components/Results.vue";
import BtnPlayAgain from "@/components/BtnPlayAgain.vue";
import Footer from "@/components/Footer.vue";
import UserPicked from "@/components/UserPicked.vue";
export default {
  data() {
    return {
      isResults: false,
      userPicked: "",
      housePicked: "",
      results: "",
      score: 0,
    };
  },
  methods: {
    gameStart(userPicked) {
      this.userPicked = userPicked;
      this.housePick();
      this.isResults = true;
      this.gameRules();
    },
    housePick() {
      let randomPick = ["paper", "scissors", "rock"];
      let randomItem = randomPick[Math.floor(Math.random() * randomPick.length)];
      this.housePicked = randomItem;
    },
    gameRestart() {
      this.userPicked = "";
      this.housePicked = "";
      this.isResults = false;
    },
    gameRules() {
      if (this.userPicked === this.housePicked) {
        this.results = "DRAW";
      } else if (this.userPicked === "paper" && this.housePicked === "rock") {
        this.results = "YOU WIN";
        this.gameScore();
      } else if (this.userPicked === "scissors" && this.housePicked === "paper") {
        this.results = "YOU WIN";
        this.gameScore();
      } else if (this.userPicked === "rock" && this.housePicked === "scissors") {
        this.results = "YOU WIN";
        this.gameScore();
      } else {
        this.results = "YOU LOSE";
      }
    },
    gameScore() {
      this.score++;
    },
  },
  mounted() {
    if (localStorage.score) {
      this.score = localStorage.score;
    }
  },
  watch: {
    score(newScore) {
      localStorage.score = newScore;
    },
  },
  components: {
    Score,
    Results,
    BtnPlayAgain,
    Footer,
    UserPicked,
  },
};
</script>
