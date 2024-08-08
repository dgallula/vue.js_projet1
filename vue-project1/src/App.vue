<template>
  <p>
    Compteur: {{ count }}
  </p>
  <div v-if="count > 5">

    <p>Bravo , vous avez cliqué sur le bouton plus de 5 fois </p>
  </div>
  <div v-else>
    <p> Vous avez cliqué sur le bouton moins de 5 fois </p>
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



