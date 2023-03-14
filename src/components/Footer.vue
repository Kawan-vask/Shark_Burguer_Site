

<!-- 1 -->


<template><!--TEMPLATE---------------------------------------------->
    
    <footer id="footer">

        <a href="https://www.sharkdata.com.br" target="_blank" id="sharklink">&copy; 2023 Shark Burguer</a>

    </footer>

</template>
<!--=============================================================-->


<!-- 2 -->


<!--SCRIPT--------------------------------------------------------->
<script>

    export default {
        name: 'Footer'

    }
</script>
<!--=============================================================-->


<!-- 3 -->


<!--STYLE---------------------------------------------------------->
<style scoped>

    #footer{

      height: 150px;
      background-color: #242425;
      border-top: 4px solid #111;
      color: #efa335;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 100%;
      border-top: 2px #efa335 solid;

    }

    #sharklink{

        color: #efa335;
        text-decoration: none;
        margin: 10px;

    }

    #sharklink:hover{

        transition: .3s;
        color: white;

    }

</style>
<!--=============================================================-->