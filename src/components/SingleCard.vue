<template>
  <section class="SingleCard sp-container d-flex justify-content-center align-content-center flex-wrap py-5">


    <!-- BLOCCO FILM  -->
    <div class="row justify-content-center w-100">
      <h2 class="d-block text-center">FILM</h2>

      <!--Ciclo Film -->
      <div
      v-for="(el) in movieSearched"
      :key='el.id'
      class="m-3 flip-card">

        <div class="flip-card-inner">

          <!-- Inserimento Poster  -->
          <div class="flip-card-front">
            <img v-if="el.poster_path" class="poster" 
            :src="`https://image.tmdb.org/t/p/w500/${el.poster_path}`" 
            :alt="`${el.title}`">

            <div v-else class="poster">
              <span>{{el.title}}</span>
            </div>
          </div>

          <!-- Parte Inferiore della Card  -->
          <div class="flip-card-back"
          :style="setBgImage(`https://image.tmdb.org/t/p/w500/${el.poster_path}`)">

            <div class="overlay">
              <li class="box-title">
                <h6>Title:</h6>
                <span>{{el.title}}</span>
              </li>

              <li class="h-10 box-original-title">
                <h6>Original Title:</h6>
                <span>{{el.original_title}}</span>
              </li>

              <!-- Lingua  -->
              <li v-if="el.original_language === 'it'"
                  class="box-language">
                <h6>Language:</h6>
                <img class="flag" :src="flagLanguageIT" :alt="el.original_language">
              </li>

              <li v-else-if="el.original_language === 'en'"
                  class="box-language">
                <h6>Language:</h6>
                <img class="flag" :src="flagLanguageEN" :alt="el.original_language">
              </li>

              <li v-else
                class="box-language">
                <h6>Language:</h6>
                <span>{{el.original_language}}</span>
              </li>

              <!-- Descrizione  -->
              <li class="description">
                <h6>Description:</h6>
                <span>{{el.overview}}</span>
              </li>

              <!-- Valutazione con stars  -->
              <li class="section-stars">
                  <h6>Vote:</h6>
                  <div class="box-stars">
                    <i v-for="(star,index) in 5"
                    :key="index"
                    class="d-inline-block fa-star"
                    :class="index < Math.round(el.vote_average / 2) ? 'fas' : 'far'">
                    </i>
                  </div>
              </li>

            </div>
          </div>
        </div>
      </div>
    </div>
    


    <!-- BLOCCO TV SERIES  -->
    <div class="row justify-content-center w-100">

      <h2 class="d-block text-center">SERIE TV</h2>


    <!--Ciclo Series -->
      <div
      v-for="(el) in seriesSearched"
      :key='el.id'
      class="flip-card m-3">

      <div class="flip-card-inner">

        <!-- Inserimento Poster  -->
        <div class="flip-card-front">
          <img v-if="el.poster_path" class="poster" 
          :src="`https://image.tmdb.org/t/p/w500/${el.poster_path}`" 
          :alt="`${el.name}`">

          <div v-else class="poster">
              <span>{{el.name}}</span>
          </div>
        </div>

    <!-- Parte Inferiore della Card  -->
        <div class="flip-card-back"
        :style="setBgImage(`https://image.tmdb.org/t/p/w500/${el.poster_path}`)">

        <div class="overlay">

          <li class="box-title">
            <h6>Title:</h6>
            <span>{{el.name}}</span>
          </li>

          <li class="h-10 box-original-title">
            <h6>Original Title:</h6>
            <span>{{el.original_name}}</span>
          </li>


        <!-- Lingua  -->
         <li v-if="el.original_language === 'it'"
            class="box-language">
            <h6>Language:</h6>
            <img class="flag" :src="flagLanguageIT" :alt="el.original_language">
          </li>

          <li v-else-if="el.original_language === 'en'"
              class="box-language">
              <h6>Language:</h6>
              <img class="flag" :src="flagLanguageEN" :alt="el.original_language">
            </li>

            <li v-else
              class="box-language">
              <h6>Language:</h6>
              <span>{{el.original_language}}</span>
            </li>

        <!-- Descrizione  -->
          <li class="description">
            <h6>Description:</h6>
            <span>{{el.overview}}</span>
          </li>


        <!-- Valutazione con stars  -->
          <li class="section-stars">
            <h6>Vote:</h6>
            <div class="box-stars">
              <i v-for="(star,index) in 5"
              :key="index"
              class="d-inline-block fa-star"
              :class="index < Math.round(el.vote_average / 2) ? 'fas' : 'far'">
              </i>
            </div>
          </li>

        </div>

         
          
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

  methods: {

    setBgImage(urlImage){
      return {
        backgroundImage: `url(${urlImage})`,
        background: `linear-gradient(rgba(255,255,255,.5), rgba(255,255,255,.5))`
      }
    }
  }

}
</script>



<style lang="scss">

@import "../assets/style/general.scss";
@import "~@fortawesome/fontawesome-free/css/all.min.css";

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
          background-size: contain;
          color: white;
          list-style: none;
          transform: rotateY(180deg);



          .overlay {
            height: 100%;
            background-color: rgba(0, 0, 0, .5)
          } 



          li {

            display: flex;
            flex-direction: column;
            align-items: center;

            h6{
              text-align: center;
              font-weight: 700;
              color: black;
              margin: 0 !important;
            }

            span{
              font-size: 11px;
              margin: 0 !important;
            }

            img.flag{
              height: 15px;
              width: 15px;
            }

            .fas.fa-star{
              color: yellow;
            }
          
          }
            

            li.box-title{
              height: 15%;
            }

            li.box-original-title{
              height: 15%;
            }

            li.box-language{
              height: 15%;
            }

            li.description {
              overflow-y: auto;
              height: 40% ;
            }

            li.section-stars {
              height: 15%;
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