<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Vue dobbelstenen"/>
    <button @click="RollDice">Rol dobbelstenen</button>
    <br><br>
    <div v-for="(n, index) in rolledNumbers" :key="index">{{ n.unicode + ': ' + n.value }}</div>
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
      console.log(this.dices);
      //let i in this.rolledNumbers

       for (let i = 0; i < 6; i++) {
        console.log(i);
        this.rolledNumbers[i].value = this.dices.filter(die => die == i).length;
      }
      console.log(this.rolledNumbers);
    }
  },

    data() {  
      return {
        dices: [],
        numberOfDices: 8,
        rolledNumbers: [
          {'eyes': 1, value: 0, unicode: '\u2680'}, 
          {'eyes': 2, value: 0, unicode: '\u2681'}, 
          {'eyes': 3, value: 0, unicode: '\u2682'}, 
          {'eyes': 4, value: 0, unicode: '\u2683'}, 
          {'eyes': 5, value: 0, unicode: '\u2684'}, 
          {'eyes': 6, value: 0, unicode: '\u2685'}
        ]
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
