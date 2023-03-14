

<!-- 1 -->


<template><!--TEMPLATE---------------------------------------------->
    
  <div>
    
    <Banner/>
    
    <div class="Main-Container">
    
      <h1 class="titulo">MONTE SEU BURGUER:</h1>  
      <burguer-form/>

    </div>

  </div>

</template>

<!--=============================================================-->


<!-- 2 -->


<!--SCRIPT--------------------------------------------------------->
<script>

  import Banner from '../components/Banner.vue';
  import BurguerForm from '../components/burguerForm.vue';

  export default {

    name:"Home",
    components:{

      Banner,
      BurguerForm
    }

  }

</script>

<!--=============================================================-->


<!-- 3 -->


<!--STYLE---------------------------------------------------------->
<style scoped>


</style>

<!--=============================================================-->