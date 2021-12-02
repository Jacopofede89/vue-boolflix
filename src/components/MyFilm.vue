<template>
  <header>
    <div class="title">
        <h2>Boolflix</h2>
    </div>
    <div id="searching">
      <form>
        <input type="text" placeholder="Cerca" v-model="title">
        <button @click.prevent="$emit('ricerca', title)">Cerca</button>
      </form>
    </div>
  </header>
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
header {
    background-color: black;
    border:solid 2px red;
    display: flex;
    justify-content: space-between;
    .title {
      h2 {
          color: red;
          font-size: 20px;
          padding: 20px;
      }
        
    }
    #searching {
      padding: 20px;
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
