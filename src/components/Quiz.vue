<script setup lang="ts">

import { computed, ref } from "vue";
import Progress from "./Progress.vue";
import Question from "./Question.vue";
import Recap from "./Recap.vue";

const state = ref('question')
const step = ref(0)
const props = defineProps<{ quiz: object }>()
const answers = ref(props.quiz.questions.map(() => null))
const question = computed(() => props.quiz?.questions[step.value]
)

const addAnswer = (answer: string) => {
  answers.value[step.value] = answer
  if (step.value === props.quiz?.questions.length -1 ) {
    state.value = 'recap'
  } else {
    step.value++
  }

}
</script>

<template>
  <div>
    <h1>
      {{ quiz?.title }}
    </h1>
    <Progress :value="step" :max="quiz?.questions.length - 1" />
    <Question :key="question.question" :question="question" v-if="state === 'question'" @answer="addAnswer" />
    <Recap v-if="state === 'recap'" :answers="answers" :quiz="quiz"/>
    {{answers}}
  </div>
</template>

<style scoped></style>