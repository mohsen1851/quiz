<template>
  <div class="ctr">
    <questions v-if="questionsAnswered<questions.length" @answer-qs="questionAnswer"
               :questions="questions" :questionAnswered="questionsAnswered"
    />
    <result v-else :result="results" :correctAnswer="totalCorrectAnswer"/>

    <button type="button" @click="reset" class="reset-btn">Reset</button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";

export default {
  name: 'App',
  components: {
    Questions, Result
  },
  data() {
    return {
      totalCorrectAnswer:0,
      questionsAnswered: 0,
      questions: [
        {
          q: 'What is 2 + 2?',
          answers: [
            {
              text: '4',
              is_correct: true
            },
            {
              text: '3',
              is_correct: false
            },
            {
              text: 'Fish',
              is_correct: false
            },
            {
              text: '5',
              is_correct: false
            }
          ]
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: '5',
              is_correct: false
            },
            {
              text: '7',
              is_correct: false
            },
            {
              text: '6',
              is_correct: true
            },
            {
              text: '12',
              is_correct: false
            }
          ]
        },
        {
          q: 'Find the missing letter: C_ke',
          answers: [
            {
              text: 'e',
              is_correct: false
            },
            {
              text: 'a',
              is_correct: true
            },
            {
              text: 'i',
              is_correct: false
            }
          ]
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!"
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!"
        }
      ]
    }
  },
  methods:{
    questionAnswer(is_correct){
      if(is_correct)
        this.totalCorrectAnswer++

      this.questionsAnswered++
    },
    reset(){
      this.totalCorrectAnswer=0;
      this.questionsAnswered=0;
    }
  }
}
</script>

<style scoped>

</style>
