<script setup lang="ts">
import { computed, ref } from 'vue';


const props = defineProps({
  question: Object
})

const emits = defineEmits(['answer'])
const answer = ref(null)
const hasAnswer = computed(() => answer.value !== null)

</script>

<template>
  <div class="question">
    <h3>{{ question?.question }}</h3>
    <ul>
      <li v-for="(choice, index) in question?.choices" :key="choice">
        <label :for="`answer${index}`">
          <input type="radio" name="answer" :id="`answer${index}`" v-model="answer" :value="choice">
          {{ choice }}
        </label>
      </li>
    </ul>
    <button :disabled="!hasAnswer" @click="emits('answer', answer)" class="primary">Question suivante</button>
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