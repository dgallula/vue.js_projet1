<template>
  <p>Compteur: {{ count }}</p>
   <button @click="increment">Incrementer</button>
  <button @click="decrement">Décrémenter</button>
  <ul>
    <li v-for="movie in movies" 
    :key="movie.title">
      {{ movie.title }} ({{ movie.year }}) 
       <button @click="addMovie(movie)">Ajouter</button>
      <button @click="deleteMovie(movie)">Supprimer</button>
      <button @click="sortMovies(movie)">Trier</button>
    <form action="@submit.prevent" @submit="addMovie(movie)">
      <input type="text" placeholder="Titre" v-model="movie.title">
      {{ movie.title }}
      <input type="number" placeholder="Année" v-model="movie.year">
      {{ movie.year }}
      <button>Enregistrer</button>
    </form>
    </li>

  </ul>
</template>

<script setup>
import { ref } from 'vue'

// Définir la variable réactive 'count'
const count = ref(0)

const movies = ref([
  {
    title: 'Titanic',
    year: 1994
  },
  {
    title: 'The Matrix',
    year: 1972
  },
  {
    title: 'lilo & Stitch',
    year: 1974
  },
  {
    title: 'The Dark Knight',
    year: 2008
  },
  {
    title: '12 Angry Men',
    year: 1957
  }
])

// Définir la fonction 'increment'
const increment = (event) => {
  console.log(event)
  count.value++
}

const decrement = (event) => {
  console.log(event)
  count.value--
}

const deleteMovie = (movie) => {
  movies.value = movies.value.filter(m => m !== movie)
}

const addMovie = (movie) => {
  movies.value.push(movie)
  console.log(movie)
  movie.title = prompt('Entrez un nouveau titre')
  movie.title.value= ""
}

const sortMovies = ()=> {
  movies.value.sort((a, b) => a>b ? 1 : -1)
}






</script>

<style>
/* Styles ici */
</style>



