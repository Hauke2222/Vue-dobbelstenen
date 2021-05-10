<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Vue dobbelstenen"/>
    <button @click="RollDice">Rol dobbelstenen</button>
    <br><br>
    <div v-for="(n, index) in rolledNumbers" :key="index">{{ index + ': ' + n }}</div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
  },

  methods: {
    RollDice() {  
      for (let i = 0; i < this.numberOfDices; i++) {
        this.dices[i] = Math.floor(Math.random() * 6) + 1;
      }

      for (let i in this.rolledNumbers) {
        this.rolledNumbers[i] = this.dices.filter(die => die == i).length
      }
    }
  },

    data() {  
      return {
        dices: [],
        numberOfDices: 8,
        rolledNumbers: {
          1:0, 
          2:0, 
          3:0, 
          4:0, 
          5:0, 
          6:0
        }
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
