<template>
  <div class="card">
            <img
              class="card--image"
              :src="`https://image.tmdb.org/t/p/w185_and_h278_bestv2/${poster_path}`"
              alt='movie image'
            />
            <div class="card--content">
              <h3 class="card--title">{{ title }}</h3>
              <p><small>RELEASE DATE: {{ release_date }}</small></p>
              <p><small>RATING: {{ vote_average }}</small></p>
              <p class="card--desc">{{ overview }}</p>
            </div>
          </div>
</template>

<script>
  export default {
    name: 'MovieCard',
    props: {
        title: String,
        release_date: String,
        vote_average: Number,
        overview: String,
        poster_path: String,

    }
  }
</script>

<style lang="scss" scoped>

</style>
