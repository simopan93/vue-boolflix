<template>
  <main>
    <SingleCard />

  </main>
</template>




<script>
// import axios from "axios";
import SingleCard from "./SingleCard.vue";



export default {
  name: "Main",

  components: {
    SingleCard,
  }

}
</script>




<style>
  main{
    height: calc(100vh - 80px);
    background-color: grey;
  }

</style>