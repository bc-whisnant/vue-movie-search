<template>
  <div>
    <form class="form" @submit="searchMovie">
        <label for="query" class="label">
          Movie Name
        </label>
        <input
          type="text"
          placeholder="i.e. Jurassic Park"
          class="input"
          v-model="form.query"
        />
        <button class="button" type="submit">
          Search
        </button>
      </form>
      <div class="card-list">
        <MovieCard v-for="movie in movies" :key="movie.id" :poster_path="movie.poster_path" :title="movie.title" :release_date="movie.release_date" :vote_average="movie.vote_average" :overview="movie.overview"  />
      </div>

  </div>
</template>

<script>
  import axios from 'axios'
  import MovieCard from './MovieCard'
  export default {
    name: 'SearchMovies',
    data() {
      return {
        movies: [],
        form: {
           query: ''
        }
      }
    },
    components: {
      MovieCard
    },
    methods: {
      searchMovie(e) {
        e.preventDefault()
        console.log('testing 123')

        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=27850d20f9f0225c993fb660bdc67b65&language=en-US&query=${this.form.query}&page=1&include_adult=false`)
          .then(res => {
            this.movies = res.data.results
            console.log(this.movies)
          }),
          (error) => {
            console.log(error);
          }
       
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
