<template>
  <p>Compteur: {{ count }}</p>
  <div v-html="firstname"></div>
  <button @click="increment">Incrementer</button>
  <button @click="decrement">Décrémenter</button>
</template>

<script setup>
import { ref } from 'vue'

// Définir la variable réactive 'count'
const count = ref(0)

const firstname = `<span>Hello</span>`

// Définir la fonction 'increment'
const increment = (event) => {
  console.log(event)
  count.value++
}

const decrement = (event) => {
  console.log(event)
  count.value--
}

</script>

<style>
/* Styles ici */
</style>

