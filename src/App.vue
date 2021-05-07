<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Vue dobbelstenen"/>
    <button @click="RollDice">Rol dobbelstenen</button>
  </div>
</template>

<script>
//import DisplayResult from './components/DisplayResult.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    //DisplayResult,
  },

  methods: {
    RollDice() {  
      //let rolledNumbers = [0, 0, 0, 0, 0, 0];

      for (let i = 0; i < this.dices.length; i++) {
        this.dices[i] = Math.floor(Math.random() * 6) + 1;
      }
      this.dices = this.dices.sort();
    }
  },

    data() {
      return {
        dices: [0, 0, 0, 0, 0, 0]
    }
  },
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
