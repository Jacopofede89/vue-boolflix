<template >
  <div class="movies">
    <h2>{{ details.title }}</h2>
    <h4>{{ details.original_language }}</h4>
    <h4>{{ details.vote_average }}</h4>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    details: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.movies {
  img {
    width: 20px;
  }
}
</style>
