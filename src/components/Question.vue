<script setup lang="ts">
import {computed, onMounted, onUnmounted, ref} from 'vue';
import { shuffleArray } from "../functions/array.ts";
import Answer from "./Answer.vue";


const props = defineProps<{
  question: object
}>()

const emits = defineEmits(['answer'])
const answer = ref<string | null>(null)
const hasAnswer = computed(() => answer.value !== null)
const randomChoices = computed(() => shuffleArray(props.question.choices))
let timer: ReturnType<typeof setTimeout>;

const onAnswer = () => {
  clearTimeout(timer)
  timer = setTimeout(() => {
    emits('answer', answer.value)
  }, 1_500)
}
onMounted(() => {
  timer = setTimeout(() => {
    answer.value = ''
    onAnswer()
  }, 5_000)
})

onUnmounted(() => {
  clearTimeout(timer)
})

</script>

<template>
  <div class="question">
    <h3>{{ question?.question }}</h3>
    <ul>
      <li v-for="(choice, index) in randomChoices" :key="choice">
        <Answer
          :id="`answer${index}`"
          :disabled="hasAnswer"
          :value="choice"
          @change="onAnswer"
          :correctAnswer="question.correct_answer"
          v-model="answer"
        />
      </li>
    </ul>
<!--
    <button :disabled="!hasAnswer" @click="emits('answer', answer)" class="primary">Question suivante</button>
-->
  </div>
</template>

<style scoped>
.question {
  padding-top: 2rem;
  display: flex;
  flex-direction: column;
  width: 80%;
  justify-content: center;
  align-items: center;
}

.question button {
  margin-left: auto;
  margin-top: 2rem;
  display: block;
  padding: 14px 40px;
  background-color: #FF9500;
  color: #13171f;
  transition-duration: 0.4s;
  font-weight: 600;
}

.question button:hover {
  background-color: transparent;
  color: #FF9500;
  border: solid 1px #FF9500;
}

ul,
li,
a {
  list-style: none;
}
</style>