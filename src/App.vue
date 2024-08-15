<template>
  <Layout>
    <template v-slot:main>
      <div v-if="state === 'error'">
        Impossible de charger le quiz
      </div>
      <div :aria-busy="state === 'loading'">
        <div class="container">
          <Quiz :quiz="quiz" v-if="quiz" />
        </div>
      </div>
    </template>
  </Layout>
</template>

<script setup>
import { ref, onMounted } from "vue"

import Layout from "./components/Layout.vue"
import Quiz from "./components/Quiz.vue";

const quiz = ref(null)
const state = ref('loading')

onMounted(() => {
  fetch("/quiz.json")
    .then((response) => {
      if (!response.ok) {
        throw new Error("Impossible d'afficher le fichier json");
      }
      return response.json()
    })
    .then(data => {
      quiz.value = data
      state.value = "idle"
    })
    .catch(error => {
      console.error(error)
      state.value = "error"
    })

})

</script>

<style>
.container {
  margin-top: 2rem;
  text-align: left;

}
</style>