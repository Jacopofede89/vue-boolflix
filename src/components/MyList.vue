<template>
  <main>
    <section>
      <Movie v-for="(film, i) in movies" :key="i" :details="film" />
    </section>
    <section>
      <Movie v-for="(tv, i) in tvShow" :key="i" :details="tv" :isTv="true" />
    </section>
  </main>
</template>

<script>
import Movie from "@/components/Movie.vue";

export default {
  name: "MyList",
  components: {
    Movie,
  },
  props: {
    movies: Array,
    tvShow: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
main {
  padding: 15px;
  background-color: black;
}
</style>
