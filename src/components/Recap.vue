<script setup lang="ts">
import {computed} from "vue";

const props = defineProps({
  quiz: Object,
  answers: Array
})

const score = computed(() => {
  return props.quiz.questions.reduce((acc: number, question: Object, k: number) => {
    if (question.correct_answer === props.answers[k]) {
      return acc + 1
    }
    return acc
  }, 0)
})

const hasWon = computed(() => score.value >= props.quiz.minimum_score)
</script>

<template>
  <div>
    <h1>Recap</h1>
    <p>
      Score : {{score}}/{{quiz?.questions.length}}
    </p>
    <p>
      {{ hasWon ? quiz.success_message: quiz.failure_message}}
    </p>
  </div>
</template>

<style scoped>

</style>