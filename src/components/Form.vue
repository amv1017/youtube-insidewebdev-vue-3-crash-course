<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  inputValue: {
    type: String,
    required: true
  }
})

const emit = defineEmits([
  'submit'
])

</script>

<template>
  <h1>Form</h1>
  <form @submit.prevent="(e) => emit('submit', e)">
    <input type="text" :value="props.inputValue">
    <input type="submit">
  </form>
</template>

<style>
</style>
