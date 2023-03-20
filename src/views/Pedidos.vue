

<!-- 1 -->


<template><!--TEMPLATE---------------------------------------------->
    
  <div class="Main-Container">
    <h1 id="titulo">GERENCIAR PEDIDOS:</h1>
    
    <Dashboard/>

  </div>

</template>

<!--=============================================================-->


<!-- 2 -->


<!--SCRIPT--------------------------------------------------------->
<script>

  import Dashboard from '../components/Dashboard.vue';

  export default {
    name:"Pedidos",

    components:{

      Dashboard,

    }
  }
</script>

<!--=============================================================-->


<!-- 3 -->


<!--STYLE---------------------------------------------------------->
<style scoped>

  #titulo{

    color: #efa335;

  }

</style>

<!--=============================================================-->