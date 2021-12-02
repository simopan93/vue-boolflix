<template>
  <div>
    <Header @nameSearch = "userSearch" />
    <Main 
    :movieSearched = "movieSearched"
    :seriesSearched = "seriesSearched"/>
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
      apiUrlMovie: "https://api.themoviedb.org/3/search/movie",
      apiParamsMovie :{
        api_key: "3f7c87f58d989212050b3b07d574df2e",
        language: "it-IT",
        query: "",
      },

      apiUrlSeries: "https://api.themoviedb.org/3/search/tv",
      apiParamsSeries :{
        api_key: "3f7c87f58d989212050b3b07d574df2e",
        language: "it-IT",
        query: "",
      },
      
      movieSearched: [],
      seriesSearched: []
    }
  },

  methods:{
    userSearch(name){
     this.fillArrayMovie(name);
     this.fillArraySeries(name);
    },


    fillArrayMovie(name){
      this.apiParamsMovie.query = name;
      
      axios.get(this.apiUrlMovie, {params: this.apiParamsMovie})
      .then ( r => {
        console.log("Api chiamato dentro App" ,name ,r.data.results);
        this.movieSearched = r.data.results;
        console.log("Log di MovieSearched" ,name ,this.movieSearched);

      }).catch( error => {
            console.log(error);
        });
    },


    fillArraySeries(name){
      this.apiParamsSeries.query = name;
      
      axios.get(this.apiUrlSeries, {params: this.apiParamsMovie})
      .then ( r => {
        console.log("Api chiamato dentro App" ,name ,r.data.results);
        this.seriesSearched = r.data.results;
        console.log("Log di seriesSearched" ,name ,this.seriesSearched);

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
