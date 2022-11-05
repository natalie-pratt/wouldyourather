<template>
  <div id="app">

      <h1 id="wyr-h1">Would you rather...</h1>

      <would-you-rather v-bind:question="wyrQuestion"
        v-bind:answer1="wyrAnswer1"
        v-bind:answer2="wyrAnswer2"
        v-on:answer-changed="answerChanged">
      </would-you-rather>

      <p id="user-selection-msg-p">{{userSelectionMsg}}</p>
  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: 'Would you rather be incredibly funny or incredibly smart?',
      wyrAnswer1: 'Incredibly funny',
      wyrAnswer2: 'Incredibly smart',
      userSelectionMsg: ''
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMsg = `Thanks! You chose ${choice}.`
    }
  }
}
</script> 
 
<style>

body {
  background-color: rgb(153, 190, 171);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #213433;
  margin-top: 70px;
  background-color: rgb(26, 59, 49);
}

#user-selection-msg-p {
  color: white;
  padding: 20px 0 32px;
  font-size: 18px;
}

#wyr-h1 {
  margin: 30px 100px 0px;
  padding: 20px;
  background-color: white;
}
</style>
