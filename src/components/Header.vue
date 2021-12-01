<template>
  <header class="d-flex align-items-center justify-content-between px-4">
    <h1>LOGO BOOLSTRAP</h1>

    <input type="text"
    v-model="nameSearch"
    @keyup.enter="$emit('nameSearch' ,nameSearch)">
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

header {
  height: 80px;
  background-color: black;

  h1 {
    color: white;
  }
}

</style>