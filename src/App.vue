<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Vue dobbelstenen" />
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
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld, // todo: kies duidelijk omschrijvende naam, bijv.: ShowMessage
  },

  methods: {
    RollDice() {
      for (let i = 0; i < this.numberOfDices; i++) {
        this.dices[i] = Math.floor(Math.random() * 6) + 1;
        // todo: onderstaande telling voor rolledNumbers kun je in deze for-loop integreren om 1 for-loop uit te sparen
      }
      // todo: reset this.rolledNumbers voor iedere worp, anders blijft deze doortellen
      for (let i = 0; i < this.dices.length; i++) {
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
