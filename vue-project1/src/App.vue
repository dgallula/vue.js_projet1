<template>
  <p>Count is: {{ count }}</p>
  <div v-if="count >5 " class="text-red-500">
    <p>You clicked more than 5 times</p>
  </div>
  <div v-else class="text-green-500">
    <p>You clicked less than 5 times</p>
  </div>
  
  <button @click="increment">Incrementer</button>
  <button @click="decrement">Décrémenter</button>
</template>

<script setup>
import { ref } from 'vue'

// Définir la variable réactive 'count'
const count = ref(0)

// Définir la fonction 'increment'
const increment = () => {
  count.value++
}

const decrement = () => {
  count.value--
}

</script>

<style>
/* Styles ici */
</style>



