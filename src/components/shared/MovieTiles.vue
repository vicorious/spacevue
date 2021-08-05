<template>
  <section class="movieTile">
    <h2 class="container">{{ title }}</h2>
    <div class="movieTile__tile container">
      <router-link
        v-for="(data, index) in apiData"
        :key="index"
        :to="{ name: 'detail', params: { id: index } }"
        class="movieTile__link"
        draggable="false"
      >
              <img
          :src="`https://image.tmdb.org/t/p/w200/q6y0Go1tsGEsmtFryDOJo3dEmqu.jpg`"
          :alt="data.name || data.title"
          :title="data.name || data.title"
          class="upcommingMovies__poster"
          loading="lazy"
          draggable="false"
        />
        <span class="movieTile__name"> {{ index + 1 }}. {{ data.Production_Company }} </span>
        <span class="movieTile__type" :title="data.Production_Company">
          {{ data.Writer}}
        </span>
      </router-link>
    </div>
  </section>
</template>

<script>
import { onMounted, ref } from "vue";
import json from '../../db/Film_Locations_in_San_Francisco.json'

export default {
  props: { title: String, apiQuery: String, img: {type: String, default : "https://image.tmdb.org/t/p/w200/2nruTQOL4qxNF4wOTYZVDV4tP3N.jpg" } },
  img(){
    let number = Math.floor(Math.random() * (10 - 1 + 1)) + 1;
    this.img = number % 2 == 0 ? "https://image.tmdb.org/t/p/w200/9dKCd55IuTT5QRs989m9Qlb7d2B.jpg" : "https://image.tmdb.org/t/p/w200/qAZ0pzat24kLdO3o8ejmbLxyOac.jpg";
  },
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
.movieTile {
  background: $lightbg;

  &__tile {
    display: flex;
    flex-direction: row;
    gap: 2rem;
    padding: 2rem 1rem;
    overflow-x: auto;
    overflow-y: hidden;

    &::-webkit-scrollbar {
      height: 8px;
    }

    &::-webkit-scrollbar-thumb {
      background-color: $gray;
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
    width: 200px;
    height: 300px;
    box-shadow: 0 5px 20px #000;

    &:hover {
      outline: 4px solid $green;
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

  &__type {
    position: absolute;
    bottom: 8px;
    left: 8px;
    padding: 5px;
    font-size: 12px;
    background-color: rgba(#000, 0.2);
  }

  &__rating {
    position: absolute;
    right: 8px;
    bottom: 8px;
    padding: 5px;
    font-size: 12px;
    background-color: rgba(#000, 0.2);
  }
}
</style>
