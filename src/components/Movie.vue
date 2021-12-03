<template >
  <!-- movies -->
  <main>
    <div v-if="!isTv" class="movies">
      <img v-if="details.backdrop_path === null" src="https://www.macitynet.it/wp-content/uploads/2016/06/netflix-logo-930x930.png"/>
      <img v-else :src="ImgUrl + details.poster_path" alt="" />
      <div class="info_card">
        <h2>Titolo: {{ details.title }}</h2>
        <h2>Titolo orginale: {{ details.original_title }}</h2>
      <span>
        Lingua:
        <img class="flag" :src="ImgUrl.original_language === 'it' ? require('../assets/ita.png'): require('../assets/uk.png')"/>
      </span>
      <!-- <h4>Voto: {{ details.vote_average }}</h4> -->
      <h3>Voto: <star-rating :rating="vote()" :star-size="15"  :show-rating="false" :read-only="true"/></h3>
      <p v-if="details.overview === '' "><strong>Overview:</strong> Non disponibile</p>
      <p v-else><strong>Overview:</strong> {{ details.overview }}</p>
      </div>
    </div>

    <!-- tv show -->
    <div v-if="isTv" class="tv">
      <img v-if="details.backdrop_path === null" src="https://www.macitynet.it/wp-content/uploads/2016/06/netflix-logo-930x930.png"/>
      <img v-else :src="ImgUrl + details.poster_path" alt=""/>
      <div class="info_card">
        <h2>Titolo: {{ details.name }}</h2>
      <h4>Titolo orginale: {{ details.original_name }}</h4>
      <span>Lingua:<img class="flag" :src="details.original_language === 'it' ? require('../assets/ita.png'): require('../assets/uk.png')"/></span>
      <h3>Voto:<star-rating :rating="vote()" :star-size="15" :show-rating="false" :read-only="true"/></h3>
      <p v-if="details.overview === '' "><strong>Overview:</strong> Non disponibile</p>
      <p v-else><strong>Overview:</strong> {{ details.overview }}</p>
      </div>
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
  height: 450px;
  padding: 15px;
  float: left;
  margin: 20px;
  
  .flag {
    width: 20px;
    height: 20px;
  }
  img {
    width: 100%;
    height: 100%;
    
  }
  .movies,.tv{
    position: relative;
  }
  .info_card {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: 0;
  transition: .5s ease;
  background-color:black;
  text-align: initial;
  font-size:15px ;
  overflow:hidden;
}
.movies:hover .info_card {
  opacity: 1;
}
.tv:hover .info_card {
  opacity: 1;
}
}
</style>
