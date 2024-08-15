<script setup lang="ts">
import { computed } from "vue";

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
    <div class="recap">
      <p class="score">
        Score : {{ score }}/{{ quiz?.questions.length }}
      </p>
      <h1 class="result">
        {{ hasWon ? quiz.success_message : quiz.failure_message }}
      </h1>
    </div>
  </div>
</template>

<style scoped>
.recap {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.recap p {
  margin-top: 40px;
  font-size: 2rem;
  font-weight: 500;
}

.recap h1 {
  margin-top: 60px;
  font-size: 40px;
  font-weight: 700;
}
</style>