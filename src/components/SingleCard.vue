<template>
  <section class="SingleCard container d-flex justify-content-center align-content-center flex-wrap py-5">

    <ul
    v-for="(el, index) in movieSearched"
    :key='index'
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


  </section>
</template>



<script>
export default {
  name: "SingleCard",

  props: {
    movieSearched: Array
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