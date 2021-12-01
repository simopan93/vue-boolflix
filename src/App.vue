<template>
  <div>
    <Header @nameSearch = "userSearch">
    <Main />
  </div>
</template>

<script>

import axios from "axios";
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"


export default {
  name: 'App',

  components: {
    Header,
    Main
  },

  data(){
    return{
      api_url: "https://api.themoviedb.org/3/search/movie?",
      api_key: "3f7c87f58d989212050b3b07d574df2e",
      filmOrMovieSearch: "",
    }
  },

  methods:{
    userSearch(name){

    }
  }


}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";

</style>
