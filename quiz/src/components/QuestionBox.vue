<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template slot="lead">
        {{currentQuestion.question}}
      </template>

      <hr class="my-4">
      <b-list-group>
        <b-list-group-item 
          v-for="(answer,i) in answers" 
          :key="i" 
          @click="selectAnswer(i)" 
          :class="[selectedIndex === i ? 'selected' : '']"
          
          >
          {{answer}}
        </b-list-group-item>
      </b-list-group>

      <b-button variant="primary" href="#">Submit</b-button>
      <b-button @click="next" variant="success" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
import _ from 'lodash'

export default({
 props:{
   currentQuestion: Object,
   next: Function
 },
 data(){
   return{
     selectedIndex: null,
     shuffledAnswers: []
   }
 },
 watch: {
   currentQuestion(){
     this.selectedIndex = null
     this.shuffleAnswers()
   }
 },
 computed: {
   answers(){
     let answers = [...this.currentQuestion.incorrect_answers]
     answers.push(this.currentQuestion.correct_answer)
     return answers
   }
 },
 methods:{
   selectAnswer(i) {
     this.selectedIndex = i
   },
   shuffleAnswers(){
     let answers = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer]
     this.shuffledAnswers = _.shuffle(answers)
   }
 }
})
</script>

<style scoped>
  .list-group{
    margin-bottom: 15px; 
  }

  .btn{
    margin: 0 5px
  }

  .list-group-item:hover{
    background: #eee;
    cursor: pointer; 
  }

  .selected{
    background-color: lightblue; ;
  }

  .correct {
    background-color: green;
  }

  .inCorrect {
    background-color: red;
  }
</style>