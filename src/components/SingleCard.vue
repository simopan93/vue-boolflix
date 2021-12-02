<template>
  <section class="SingleCard sp-container d-flex justify-content-center align-content-center flex-wrap py-5">

    <div class="row justify-content-center w-100">
      <h2 class="d-block text-center">FILM</h2>


      <ul
      v-for="(el) in movieSearched"
      :key='el.id'
      class="d-inline-block m-3">
        <li>{{el.title}}</li>
        <li>{{el.original_title}}</li>

        <li v-if="el.original_language === 'it'">
          <img :src="flagLanguageIT" :alt="el.original_language">
        </li>

        <li v-else-if="el.original_language === 'en'">
          <img :src="flagLanguageEN" :alt="el.original_language">
        </li>

        <li v-else>{{el.original_language}}</li>
        <li>{{el.vote_average}}</li>
      </ul>
    </div>
    



    <div class="row justify-content-center w-100">

      <h2 class="d-block text-center">SERIE TV</h2>

      <ul
      v-for="(el) in seriesSearched"
      :key='el.id'
      class="d-inline-block m-3">
        <li>{{el.name}}</li>
        <li>{{el.original_name}}</li>

        <li v-if="el.original_language === 'it'">
          <img :src="flagLanguageIT" :alt="el.original_language">
        </li>

        <li v-else-if="el.original_language === 'en'">
          <img :src="flagLanguageEN" :alt="el.original_language">
        </li>

        <li v-else>{{el.original_language}}</li>
        <li>{{el.vote_average}}</li>
      </ul>

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
    
    ul{
      width: calc(100% / 5);
      list-style: none;
      padding: 10px;
      border: 1px solid black;

      li {

        img{
          height: 15px;
          width: 15px;
        }
      }
    }
  }

</style>