<template>
  <MovieTiles
    title="Space44 Test Film Locations"
    apiQuery="trending/movie/week"
  />
  <!--MovieTiles title="Today's Trending Movies" apiQuery="trending/movie/day" />  
  <MovieTiles title="Top Rated Movies" apiQuery="movie/top_rated" /-->
  <Map/>
  <UpcomingMovies />
</template>

<script>
import MovieTiles from '@/components/shared/MovieTiles.vue'
import PopularActors from '@/components/shared/PopularActors.vue'
import UpcomingMovies from '@/components/UpcomingMovies.vue'
import Map from '@/components/shared/Map.vue';

export default {
  components: {
    MovieTiles,
    PopularActors,
    UpcomingMovies,
    Map
  },

  setup () {}
}
</script>

<style lang="scss">
*,
*::before,
*::after {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
  color: #fff;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  background: $bg;
}

.container {
  width: 100%;
  margin-right: auto;
  margin-left: auto;
  padding: 0 1rem;
}

@media (min-width: 1400px) {
  .container {
    max-width: 1320px;
  }
}
</style>
