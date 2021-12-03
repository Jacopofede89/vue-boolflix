<template>
  <div id="app">
    <MyFilm @ricerca="search"
    />
    <MyList :movies="listMovie" 
    :tvShow="listTv"/>
  </div>
</template>

<script>
import MyFilm from './components/MyFilm.vue';
import MyList from './components/MyList.vue';
import axios from "axios";

export default {
  name: 'App',
  components: {
    MyFilm,
    MyList,
  },
  data() {
    return {
      searchMovie: "",
      apiUrlmovie: "https://api.themoviedb.org/3/search/movie?api_key=8e7b0a6fcea87ee9de24d9a762df1b39&query=",
      listMovie: [],
      apiUrltv: "https://api.themoviedb.org/3/search/tv?api_key=8e7b0a6fcea87ee9de24d9a762df1b39&query=",
      listTv: [],
    }

  },
  methods: {
    getMovies() {
      axios
      .get(this.apiUrlmovie+this.searchMovie)
      .then((result) => {
        this.listMovie = result.data.results
      });
      
    },
    search(searchMovie) {
      this.searchMovie = searchMovie;
      this.getMovies();
      this.getTv();
    },
    getTv() {
      axios
      .get(this.apiUrltv+this.searchMovie)
      .then((result) => {
        this.listTv = result.data.results
      });
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:white;
}
* {
  margin: 0;
}
</style>

