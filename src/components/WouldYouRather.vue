<template>
  <div class="wyr">

    <h2 id="wyr-msg-h2">Would you rather...</h2>

    <h3 id="question-h3">{{question.wyrQuestion}}</h3>

    <input type="radio" 
      v-model="choice" 
      v-bind:value="question.wyrAnswer1" 
      v-on:change="choiceMade">
    <label>{{question.wyrAnswer1}}</label>

    <input type="radio" 
      v-model="choice" 
      v-bind:value="question.wyrAnswer2" 
      v-on:change="choiceMade">
    <label>{{question.wyrAnswer2}}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    question: Object,
  },
  data() {
    return {
      choice: ''
    }
  }, 
  methods: {
    choiceMade() {
      this.$emit('answer-changed', this.choice) // Let parent know that change event of choice has occured
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  #wyr-msg-h2 {
    padding-bottom: 5px;
  }

  #question-h3 {
    margin: 40px 0 0;
    padding-bottom: 25px;
  }
  
  .wyr {
    border: 2px solid;
    padding: 30px;
    background-color: darkslategrey;
    color: white;
  }

</style>
