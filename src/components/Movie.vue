<template >
<!-- movies -->
<main>
  <div v-if="!isTv" class="movies">
    <h2>{{ details.title }}</h2>
    <h4>{{ details.original_language }}</h4>
    <span>
      Lingua:
      <img :src="details.original_language === 'it'? require ('../assets/ita.png') : require ('../assets/uk.png')" 
      />
    </span>
    <h4>{{ details.vote_average }}</h4>
  </div>
  <!-- tv show -->
  <div v-if="isTv" class="tv">
    <h2>{{ details.name }}</h2>
    <h4>{{ details.original_language }}</h4>
    <span>
      Lingua:
      <img :src="details.original_language === 'it'? require ('../assets/ita.png') : require ('../assets/uk.png')" 
      />
    </span>
    <h4>{{ details.vote_average }}</h4>
  </div>
</main>
</template>

<script>
export default {
  name: "Movie",
  props: {
    details: Object,
    isTv: Boolean
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.movies, .tv{
  img {
    width: 20px;
  }
}
</style>
