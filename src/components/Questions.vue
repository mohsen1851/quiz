<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar" :style="{width:`${(questionAnswered/questions.length)*100}%`}"></div>
      <div class="status">{{ questionAnswered }} out of {{ questions.length }} questions answered</div>
    </div>
    <div class="single-question" v-for="(question,qi) in questions" :key="question.q" v-show="qi===questionAnswered">
      <div class="question">{{ question.q }}</div>
      <div class="answers">
        <div class="answer" v-for="answer in question.answers"
             @click="answerQs(answer.is_correct)"
             :key="answer.text">{{ answer.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Questions",
  props: ["questions", "questionAnswered"],
  emits: ['answer-qs'],
  methods: {
    answerQs(is_correct) {
      this.$emit('answer-qs',is_correct);
    }
  }
}
</script>

<style scoped>

</style>