<script setup lang="ts">
defineProps({
  value: Number,
  max: Number
})
</script>

<template>
  <div class="progress">
    Etape {{ value + 1 }}/{{ max + 1 }}
    <progress :value="value" :max="max"></progress>
  </div>
</template>

<style scoped>
.progress {
  margin-top: 2rem;
}

progress {
  margin-top: 1rem;
}
</style>