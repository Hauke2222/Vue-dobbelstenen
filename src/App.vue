<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <ShowMessage msg="Vue dobbelstenen" />
    <button @click="RollDice">Rol dobbelstenen</button>
    <br /><br />
    <div
      style="font-size: 32px"
      v-for="(n, index) in rolledNumbers"
      :key="index"
    >
      {{ n.unicode + ": " + n.value }}
    </div>
  </div>
</template>

<script>
import ShowMessage from "./components/ShowMessage.vue";

export default {
  name: "App",
  components: {
    ShowMessage,
  },

  methods: {
    RollDice() {
      Object.assign(this.$data, this.$options.data.apply(this)); // Resets this.rolledNumbers
      for (let i = 0; i < this.numberOfDices; i++) {
        this.dices[i] = Math.floor(Math.random() * 6) + 1;
        this.rolledNumbers[this.dices[i] - 1].value++;
      }
    },
  },

  data() {
    return {
      dices: [],
      numberOfDices: 8,
      rolledNumbers: [
        { eyes: 1, value: 0, unicode: "\u2680" },
        { eyes: 2, value: 0, unicode: "\u2681" },
        { eyes: 3, value: 0, unicode: "\u2682" },
        { eyes: 4, value: 0, unicode: "\u2683" },
        { eyes: 5, value: 0, unicode: "\u2684" },
        { eyes: 6, value: 0, unicode: "\u2685" },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
</style>
