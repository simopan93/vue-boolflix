<template>
  <section class="SingleCard sp-container d-flex justify-content-center align-content-center flex-wrap py-5">


    <!-- BLOCCO FILM  -->
    <div class="row justify-content-center w-100">
      <h2 class="d-block text-center">FILM</h2>


      <div
      v-for="(el) in movieSearched"
      :key='el.id'
      class="m-3 flip-card">

        <div class="flip-card-inner">

          <div class="flip-card-front">
            <img class="poster" 
            :src="`https://image.tmdb.org/t/p/w500/${el.poster_path}`" 
            :alt="`${el.title}`">
          </div>


          <div class="flip-card-back">
            <li>{{el.title}}</li>
            <li>{{el.original_title}}</li>

            <li v-if="el.original_language === 'it'">
              <img class="flag" :src="flagLanguageIT" :alt="el.original_language">
            </li>

            <li v-else-if="el.original_language === 'en'">
              <img class="flag" :src="flagLanguageEN" :alt="el.original_language">
            </li>

            <li v-else>{{el.original_language}}</li>
            <li>{{el.vote_average}}</li>
          </div>
          
        </div>

        
      </div>
    </div>
    


    <!-- BLOCCO TV SERIES  -->

    <div class="row justify-content-center w-100">

      <h2 class="d-block text-center">SERIE TV</h2>

      <div
      v-for="(el) in seriesSearched"
      :key='el.id'
      class="flip-card m-3">

      <div class="flip-card-inner">

        <div class="flip-card-front">
          <img class="poster" 
          :src="`https://image.tmdb.org/t/p/w500/${el.poster_path}`" 
          :alt="`${el.title}`"> 
        </div>


        <div class="flip-card-back">
          <li>{{el.name}}</li>
          <li>{{el.original_name}}</li>

          <li v-if="el.original_language === 'it'">
            <img class="flag" :src="flagLanguageIT" :alt="el.original_language">
          </li>

          <li v-else-if="el.original_language === 'en'">
            <img class="flag" :src="flagLanguageEN" :alt="el.original_language">
          </li>

          <li v-else>{{el.original_language}}</li>
          <li>{{el.vote_average}}</li>
        </div>
        

      </div>

        
      </div>

    </div>

  </section>
</template>



<script>
export default {
  name: "SingleCard",

  props: {
    movieSearched: Array,
    seriesSearched: Array
  },

  data(){
    return{
      flagLanguageIT: require('../assets/img/it.png'),
      flagLanguageEN: require('../assets/img/en.png'),
    }
  },

}
</script>



<style lang="scss">

@import "../assets/style/general.scss";

  section.SingleCard {
    
    .flip-card{
      width: calc(100% / 5);
      min-width: 200px;
      height: 300px;
      background-color: transparent;
      border: 1px solid black;
      padding: 0 !important;


      .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;


        .flip-card-front{
          background-color: #bbb;

          img.poster{
            width: 100%;
            height: 300px;
          }
        }


        .flip-card-back{
          background-color: dodgerblue;
          color: white;
          list-style: none;
          transform: rotateY(180deg);


          li {

            img.flag{
              height: 15px;
              width: 15px;
            }
          }
        }
      } 
    }

    .flip-card:hover .flip-card-inner {
      transform: rotateY(180deg);
    }

    .flip-card-front, .flip-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
    }
  }

</style>