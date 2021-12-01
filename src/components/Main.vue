<template>
  <main>
    <SingleCard 
    :movieSearched = "movieSearched"/>

  </main>
</template>




<script>
// import axios from "axios";
import SingleCard from "./SingleCard.vue";



export default {
  name: "Main",

  props: {
    movieSearched: Array
  },

  components: {
    SingleCard,
  }

}
</script>




<style lang="scss">
  main{
    overflow: auto;
    height: calc(100vh - 80px);
    background-color: grey;
  }

</style>