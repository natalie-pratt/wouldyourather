<template>
  <div id="app">

      <h1 id="wyr-h1">Would you rather?</h1>

      <would-you-rather
        v-for="question in questions"
        v-bind:key="question.id"
        v-bind:wyr-question="question.wyrQuestion"
        v-bind:wyr-answer-one="question.wyrAnswer1"
        v-bind:wyr-answer-two="question.wyrAnswer2"
        v-bind:user-selection-msg="question.wyrSelectionMsg"
        v-on:answer-changed="answerChanged">
        <p id="user-selection-msg-p">{{question.userSelectionMsg}}</p>
      </would-you-rather>   
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
      questions: [
        {
          id: 0,
          wyrQuestion: 'Would you rather be incredibly funny or incredibly smart?',
          wyrAnswer1: 'Incredibly funny',
          wyrAnswer2: 'Incredibly smart',
          userSelectionMsg: ''
        },
        {
          id: 1,
          wyrQuestion: 'Would you rather live in a place with a lot of trees or live in a place near the ocean?',
          wyrAnswer1: 'Live by lots of trees',
          wyrAnswer2: 'Live by the ocean',
          userSelectionMsg: ''
        },
        {
          id: 2,
          wyrQuestion: 'Would you rather be a famous inventor or a famous writer?',
          wyrAnswer1: 'Be a famous inventor',
          wyrAnswer2: 'Be a famous writer',
          userSelectionMsg: ''
        }
      ]
      
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
