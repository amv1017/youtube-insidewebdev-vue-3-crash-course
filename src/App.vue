<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
const value = Math.exp(3*Math.log(2))

const getName = () => {
  return 'Mike'
}

const compareNumbers = (a, b) => {
  return (a === b)
}

</script>

<template>
  <h1 class="red">New Project</h1>
  <div>{{'note'}}</div>  
  <div>{{ value }}</div>
  <h3>Hello, {{ getName() }}</h3>

  <div v-if="compareNumbers(10, 10)">quite right!</div>
  <div v-else>incorrect expression</div>
</template>

<style>
.red {
  color: red;
}
</style>
