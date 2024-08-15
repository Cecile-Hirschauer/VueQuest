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
interface Emits {
  (event: 'change', payload: Event): void;
}
const emits = defineEmits<Emits>()
const onChange = (event: Event) => {
  emits('change', event)
}
</script>

<template>
  <label :for="id" :class="classes">
    <input :disabled="disabled" type="radio" name="answer" :id="id" @change="onChange" :value="value" v-model="model">
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