<script setup lang="ts">
import {computed} from "vue";

const props = defineProps<{
  id: string,
  disabled: boolean,
  value: string
  correctAnswer: string
}>()

const model = defineModel()
const classes = computed(() => ({
  disabled: props.disabled,
  right: props.disabled && props.value === props.correctAnswer,
  wrong: props.disabled && props.value !== props.correctAnswer && model.value === props.value
}))
</script>

<template>
  <label :for="id" :class="classes">
    <input :disabled="disabled" type="radio" name="answer" :id="id" v-model="model" :value="value">
    {{ value }}
  </label>
</template>

<style scoped>
.disabled {
  opacity: .5;
}
.right {
  opacity: 1;
  color: lawngreen;
}

.wrong {
  opacity: 1;
  color: red;
}
</style>