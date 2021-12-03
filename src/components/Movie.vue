<template >
  <!-- movies -->
  <main>
    <div v-if="!isTv" class="movies">
      <img
        v-if="details.backdrop_path === null"
        src="https://www.macitynet.it/wp-content/uploads/2016/06/netflix-logo-930x930.png"/>
      <img v-else :src="ImgUrl + details.poster_path" alt="" />
      <h2>{{ details.title }}</h2>
      <h4>{{ details.original_language }}</h4>
      <span>
        Lingua:
        <img class="flag" :src="ImgUrl.original_language === 'it' ? require('../assets/ita.png'): require('../assets/uk.png')"/>
      </span>
      <!-- <h4>Voto: {{ details.vote_average }}</h4> -->
      <h3>Voto: <star-rating :rating="vote()" star-size="15" :show-rating="false" read-only="false"/> </h3>
    </div>

    <!-- tv show -->
    <div v-if="isTv" class="tv">
      <img
        v-if="details.backdrop_path === null"
        src="https://www.macitynet.it/wp-content/uploads/2016/06/netflix-logo-930x930.png"/>
      <img v-else :src="ImgUrl + details.poster_path" alt="" />
      <h2>{{ details.name }}</h2>
      <h4>{{ details.original_language }}</h4>
      <span>
        Lingua:
        <img class="flag" :src="details.original_language === 'it' ? require('../assets/ita.png'): require('../assets/uk.png')"/>
      </span>
      <h3>Voto:<star-rating :rating="vote()" star-size="15" :show-rating="false" read-only="false"/></h3>
    </div>
  </main>
</template>

<script>
import StarRating from 'vue-star-rating'
export default {
  name: "Movie",
  components: {
    StarRating,
  },
  props: {
    details: Object,
    isTv: Boolean,
  },
  data() {
    return {
      ImgUrl: "https://image.tmdb.org/t/p/w342",
    };
  },
  methods: {
    vote(){
      return this.details.vote_average / 2
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
main {
  width: 20%;
  height: 550px;
  float: left;
  margin: 20px;
  .flag {
    width: 20px;
  }
  img {
    width: 100%;
    height: 100%;
  }

}
</style>
