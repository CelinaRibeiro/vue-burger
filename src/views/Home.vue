<template>
  <Banner />
  <div class="main-container"> 
   <h1>Peça o seu burger:</h1>
   <p>formulário</p>
  </div>
</template>

<script>
  import Banner from "../components/Banner.vue"

  export default {
    name: "Home",
    components: {
      Banner
    }
  }
</script>
