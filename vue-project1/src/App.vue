<template>
  <div class="container">
    <p class="counter">Compteur: {{ count }}</p>
    <div class="buttons">
      <button @click="increment">Incrémenter</button>
      <button @click="decrement">Décrémenter</button>
    </div>

    <form class="movie-form" @submit.prevent="addMovie">
      <input type="text" placeholder="Titre" v-model="newMovie.title" />
      <input type="number" placeholder="Année" v-model="newMovie.year" />
      <button type="submit">Ajouter un film</button>
    </form>

    <ul class="movie-list">
      <li v-for="movie in movies" :key="movie.title">
        {{ movie.title }} ({{ movie.year }})
        <button class="delete-btn" @click="deleteMovie(movie)">Supprimer</button>
      </li>
    </ul>

    <div class="sort-buttons">
      <button @click="sortMovies">Trier par titre</button>
      <button @click="sortMoviesByYear">Trier par année</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
const movies = ref([
  { title: 'Titanic', year: 1994 },
  { title: 'The Matrix', year: 1972 },
  { title: 'Lilo & Stitch', year: 2002 },
  { title: 'The Dark Knight', year: 2008 },
  { title: '12 Angry Men', year: 1957 }
])

const newMovie = ref({ title: '', year: '' })

const increment = () => {
  count.value++
}

const decrement = () => {
  count.value--
}

const deleteMovie = (movie) => {
  movies.value = movies.value.filter(m => m !== movie)
}

const addMovie = () => {
  if (newMovie.value.title && newMovie.value.year) {
    movies.value.push({ ...newMovie.value })
    newMovie.value.title = ''
    newMovie.value.year = ''
  } else {
    alert('Veuillez remplir tous les champs')
  }
}

const sortMovies = () => {
  movies.value.sort((a, b) => a.title.localeCompare(b.title))
}

const sortMoviesByYear = () => {
  movies.value.sort((a, b) => a.year - b.year)
}
</script>

<style>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  font-family: Arial, sans-serif;
}

.counter {
  font-size: 1.5em;
  text-align: center;
  margin-bottom: 20px;
}

.buttons {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

button {
  padding: 10px 20px;
  font-size: 1em;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.movie-form {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.movie-form input {
  flex: 1;
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.movie-form button {
  padding: 10px;
  background-color: #28a745;
}

.movie-list {
  list-style: none;
  padding: 0;
}

.movie-list li {
  padding: 10px;
  margin-bottom: 10px;
  background-color: #fff;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #ccc;
}

.delete-btn {
  background-color: #dc3545;
}

.delete-btn:hover {
  background-color: #c82333;
}

.sort-buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}
</style>


