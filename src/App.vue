<template>
  <div id="app">
    <MyFilm @ricerca="Search"/>
    <MyList :movies="list" />
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
      list: [],
      searchMovie: "",
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=8e7b0a6fcea87ee9de24d9a762df1b39&query=",
    }

  },
  methods: {
    getMovies() {
      axios
      .get(this.apiUrl+this.searchMovie)
      .then((result) => {
        this.list = result.data.results
      });
    },
    Search(searchMovie) {
      this.searchMovie = searchMovie;
      this.getMovies();
    }
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
