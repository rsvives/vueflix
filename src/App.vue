<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>My movies</h1>
  <ol class="movies-container">
    <MovieCard v-for="(m, index) in movies" :key="index" :movie="m" />
  </ol>
</template>

<script>
import axios from 'axios'
import MovieCard from './components/MovieCard.vue'

export default {
  name: 'App',
  components: {
    MovieCard
  },
  data() {
    return {
      movies: []
    }
  },
  mounted() {
    axios.get('http://localhost:3001/api/movies').then(res => {
      this.movies = res.data
      console.log(res.data);
    })
  }

}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  padding: 64px;
  color: #7e8b99;
  /* margin-top: 60px; */
  background-color: #2c3e50;
  background-color: #2a323a;
}

h1 {
  color: #bac2ca;
}

img {
  width: 80px;
}

.movies-container {
  padding: 0;
  margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>
