<template>
  <div class="row mt-3">
    <div class="col text-center">
      <button class="m-3 hover icon icon-paper" @click="userPicked('paper')">
        <img src="@/assets/images/icon-paper.svg" alt="" />
      </button>
      <button class="m-3 hover icon icon-scissors" @click="userPicked('scissors')">
        <img src="@/assets/images/icon-scissors.svg" alt="" />
      </button>
      <br />
      <button class="m-3 hover icon icon-rock" @click="userPicked('rock')">
        <img src="@/assets/images/icon-rock.svg" alt="" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: "",
    };
  },
  methods: {
    userPicked(picked) {
      this.user = picked;
      this.$emit("userPicked", this.user);
    },
  },
};
</script>

<style></style>
