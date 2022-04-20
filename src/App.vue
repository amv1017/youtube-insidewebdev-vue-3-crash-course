<script setup>
import { ref, computed, watch, onMounted, onBeforeMount } from 'vue'
import Form from './components/Form.vue'

const value = Math.ceil(Math.exp(3*Math.log(2)))

const getName = () => {
  return 'Mike'
}

const compareNumbers = (a, b) => {
  return (a === b)
}

const names = ref(['Dan', 'Lindsey', 'Peter'])

const inputValue = ref(Math.floor(Math.random()*400)+100)

const handleInputChange = (e) => {
  inputValue.value = e.target.value
}

const anotherInputValue = ref(100)

const handleSubmit = (e) => {
  console.log(e)
}

const day = ref(null)

const isFriday = computed(() => day.value === 'friday')

const handleClick = (e) => {
  day.value = 'friday'
}

watch(() => day.value, () => {
  console.log('day changed')
})

onMounted(() => {
  console.log('On mounted')
})

onBeforeMount(() => {
  console.log('On before mount')
})

const handleFormSubmit = (args) => {
  console.log(args)
}

</script>

<template>
  <h1 class="header">New Project</h1>
  <div>{{'note'}}</div>  
  <div>{{ value }}</div>
  <h3>Hello, {{ getName() }}</h3>

  <div v-if="compareNumbers(10, 10)">quite right!</div>
  <div v-else>incorrect expression</div>
  <br />

  <div v-for="number in 10">{{number}}</div>
  <br />
  <div v-for="(number, index) in names">{{number}} {{index}}</div>
  <br />

  <input type="number" v-bind:value="inputValue" v-on:input="handleInputChange" />
  <h4>{{inputValue}}</h4>
  <br />

  <input type="number" v-model="anotherInputValue" />
  <h4>{{anotherInputValue}}</h4>
  <br />

  <form @submit.prevent="handleSubmit">
    <input type="text" value="some value">
    <input type="submit" name="" id="">
  </form>
  <br />

  <button @click="handleClick">Button</button>
  <h1>{{day}} => {{isFriday}}</h1>

  <Form inputValue='message' @submit="handleFormSubmit" />

</template>

<style>
.header {
  color: steelblue;
}

body {
  background: skyblue;
}
</style>
