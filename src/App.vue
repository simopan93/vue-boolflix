<template>
  <div>
    <Header @nameSearch = "userSearch" />
    <Main :movieSearched = "movieSearched"/>
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
      movieSearched: [],
    }
  },

  methods:{
    userSearch(name){
      
      axios.get(`${this.api_url}api_key=${this.api_key}&query=${name}&language=it`)
      .then ( r => {
        console.log("Api chiamato dentro App" ,name ,r.data.results);
        this.movieSearched = r.data.results;
        console.log("Log di MovieSearched" ,name ,this.movieSearched);

      }).catch( error => {
            console.log(error);
        });
    }
  }


}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";

</style>
