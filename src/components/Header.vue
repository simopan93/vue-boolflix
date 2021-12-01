<template>
  <header class="d-flex align-items-center justify-content-between px-4">
    <h1>LOGO BOOLSTRAP</h1>

  <div class="box-input">
    <input type="text"
    v-model="nameSearch"
    @keyup.enter="$emit('nameSearch' ,nameSearch)"
    class="mx-2"
    >

    <button 
    @click="$emit('nameSearch' ,nameSearch)">
      CERCA
    </button>
  </div>
    
  </header>
</template>



<script>
export default {
  name: "Header",
  
  data(){
    return{
      nameSearch:"",
    }
  },

}
</script>



<style lang="scss">

  @import "../assets/style/general.scss";

header {
  height: 80px;
  background-color: black;

  h1 {
    color: white;
  }
}

</style>