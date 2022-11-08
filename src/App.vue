<template>
  <div id="app">

      <h1 class="wyr-h1">Would you rather?</h1>

      <would-you-rather        
        v-for="question in questions"
        v-bind:question="question"
        v-bind:key="question.id"
        v-on:answer-changed="answerChanged">
      </would-you-rather> 

      <h1 class="wyr-h1">You would rather...</h1>

      <!-- Only show this message if choice made is not true - which changes when choice
          made method is called and a selection is added to list-->
      <p id="user-message" v-show="!choiceMade">Make some choices above!</p>

    <!-- Display list of user choices -->
    <ul class="userSelection">
      <li v-for="selection in userSelections" 
        v-bind:key="selection">
        {{selection}}
      </li>
    </ul>  
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
          wyrQuestion: '...be incredibly funny or incredibly smart?',
          wyrAnswer1: 'Be incredibly funny',
          wyrAnswer2: 'Be incredibly smart',
        },
        {
          id: 1,
          wyrQuestion: '...live in a place with a lot of trees or live in a place near the ocean?',
          wyrAnswer1: 'Live by lots of trees',
          wyrAnswer2: 'Live by the ocean',
        },
        {
          id: 2,
          wyrQuestion: '...be a famous inventor or a famous writer?',
          wyrAnswer1: 'Be a famous inventor',
          wyrAnswer2: 'Be a famous writer',
        }
      ],
      userSelections: [],
      choiceMade: false, 
    }
  },
  methods: {
    answerChanged(choice) {
      
      // Add user's choice to list to be displayed on page
      this.userSelections.push(choice)
      this.choiceMade = true
      
      // Ensure unique values in list (cannot add the same choice twice)
      this.userSelections = this.userSelections.filter(function (x, i, a) { 
        return a.indexOf(x) === i; 
      });

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
  background-color: rgb(26, 59, 49);
  margin-bottom: 150px;
}

#user-selection-msg-p {
  color: white;
  padding: 20px 0 32px 0px;
  font-size: 18px;
}

.wyr-h1 {
  margin: 0px 100px 0px;
  padding: 20px;
  background-color: white;
}

.userSelection {
  color: white;
  text-align: center;
  display: inline-block;
  font-size: 20px;
}

li {
  text-align: left;
}

#user-message {
  color: white;
  text-align: center;
  font-size: 20px;
}
</style>
