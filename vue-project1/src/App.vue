<template>
  <p>
    Compteur: {{ count }}
  </p>
  <div v-show="count >= 5">
    <p>Bravo , vous avez cliqué sur le bouton plus de 5 fois </p>
  </div>

  <button @click="increment">Incrementer</button>
  <button @click="decrement">Décrémenter</button>
</template>

<script setup>
import { ref } from 'vue'

// Définir la variable réactive 'count'
const count = ref(0)

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



