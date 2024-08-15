<template>
  <Layout>
    <template v-slot:main>
      <div>
        {{ quiz }}
      </div>
    </template>
  </Layout>
</template>

<script setup>
import { ref, onMounted } from "vue"

import Layout from "./components/Layout.vue"

const quiz = ref(null)

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
    })
    .catch(error => {
      console.error(error)
    })
  console.log(quiz.data)
})

</script>