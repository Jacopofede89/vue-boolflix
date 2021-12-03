<template>
  <section>
    <div class="card">
      <div class="title">Boolflix</div>
    <div id="searching">
      <form>
        <input type="text" placeholder="Cerca" v-model="title">
        <button @click.prevent="$emit('ricerca', title)">Cerca</button>
      </form>
    </div>
    </div>    
  </section>
</template>

<script>
export default {
  name: 'MyFilm',
  data() {
        return {
            title: ""
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
section {
    background-color: black;
    border:solid 5px gold;
    .card{
      width:100%;
      height: 100px;
    }
    .title {
      height:50px;
      color: gold;
      font-size: 30px;
      padding: 20px;
      float: left;
    }
    #searching {
      padding: 20px;
      float: right;
      input {
        height: 25px;
      }
      button {
        cursor: pointer;
        height: 25px;
        margin-left: 5px;
        padding: 15px;
        line-height: 10%;
      }
    }

}
</style>
