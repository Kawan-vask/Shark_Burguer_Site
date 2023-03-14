<template>
  
  <div><!--Componentes---------------------------------->

  <Navbar :logo="logo_src" :alt="app_name"/>
  <RouterView />
  <Footer />



</div>

</template>



<script>//!--Script------------------------------------>

  import { RouterLink, RouterView } from 'vue-router';
  import Navbar from './components/Navbar.vue';
  import Footer from './components/Footer.vue';
  

  export default{

    components:{

      Navbar,
      RouterView,
      RouterLink,
      Footer,
      
    },

    data(){
      return{
        logo_src: "img/logo.png",
        app_name: "Shark Burguer"
      }
      

    }

  }

  

</script>


<!--Script--------------------------------------------->
<style>
  body {
   background-color: rgb(17, 17, 17) 
  }

  *{

    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;


  }

  .Main-Container{

    margin: 80px;
    min-height: calc(100vh - 320px);
  }

  h1{
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #ffffff;

  }


</style>


