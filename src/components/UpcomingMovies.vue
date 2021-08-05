<template>
  <section class="upcommingMovies container">
    <h2>Upcoming Movies</h2>
    <div class="upcommingMovies__tile">
      <router-link
        v-for="(data, index) in apiData"
        :key="index"
        :to="`/detail/${data.index}`"
        class="upcommingMovies__link"
        draggable="false"
      >
        <img
          :src="`https://image.tmdb.org/t/p/w200/2nruTQOL4qxNF4wOTYZVDV4tP3N.jpg`"
          :alt="data.name || data.Title"
          :title="data.name || data.Title"
          class="upcommingMovies__poster"
          loading="lazy"
          draggable="false"
        />
        <span class="upcommingMovies__name">
          {{ data.Production_Company }}
        </span>
        <span class="upcommingMovies__date">
          <!-- data.release_date in DD/MM/YYY format -->
          {{ data.Production_Company }}
        </span>
      </router-link>
    </div>
  </section>
</template>

<script>
import { onMounted, ref } from "vue";
import json from '../db/flims_locations_unrated.json'

export default {
  props: { title: String, apiQuery: String, img: {type: String, default : "https://image.tmdb.org/t/p/w200/2nruTQOL4qxNF4wOTYZVDV4tP3N.jpg" } },
  setup(props) {    
    let apiData = ref([]);
    apiData = json;
    let fetchApiData = apiData;
    onMounted(fetchApiData);
    return {
      apiData,
    };
  },


};
</script>

<style lang="scss" scoped>
.upcommingMovies {
  &__tile {
    display: flex;
    flex-direction: row;
    gap: 1rem;
    padding: 1rem 0.5rem;
    overflow-x: auto;
    overflow-y: hidden;

    &::-webkit-scrollbar {
      height: 8px;
    }

    &::-webkit-scrollbar-thumb {
      background-color: #404040;
    }
  }

  &__link {
    position: relative;
    color: #fff;
    text-decoration: none;
    transition: all 50ms ease;

    &:hover {
      transform: scale(1.05);
    }
  }

  &__poster {
    width: 190px;

    &:hover {
      border: 2px solid $green;
    }
  }

  &__name {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    padding: 5px;
    text-align: center;
    text-shadow: 1px 1px 0 #404040;
    background-color: rgba(#000, 0.2);
  }

  &__date {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    padding: 5px;
    text-align: center;
    text-shadow: 1px 1px 0 #404040;
    background-color: rgba(#000, 0.2);
  }
}
</style>
