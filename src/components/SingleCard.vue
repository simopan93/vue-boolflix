<template>
  <section class="SingleCard d-flex justify-content-center align-content-center">
    <ul class="d-inline-block">
      <li>Titolo</li>
      <li>Titolo Originale</li>
      <li>Lingua</li>
      <li>Voto</li>
    </ul>
  </section>
</template>



<script>
export default {
  name: "SingleCard"
}
</script>



<style lang="scss">

@import "../assets/style/general.scss";

  section.SingleCard {
    
    ul{
      list-style: none;
      padding: 10px;
      border: 1px solid black;
    }
  }

</style>