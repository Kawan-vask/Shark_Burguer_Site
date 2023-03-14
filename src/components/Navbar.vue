<template>
    
    <div id="navBar">
        <router-link to="/" id="logoURL">
            <img :src="logo" :alt="alt" id="logo"><span id="nomeNav">Shark Burguer™</span>
            
        </router-link>

        <router-link to="/" class="botoes">Montagem</router-link>
        <p id="divisoria">|</p>
        <router-link to="/pedidos" class="botoes">Pedidos</router-link>
    </div>

</template>

<!--SCRIPT--------------------------------------------------------->
<script>

    export default {
        name: "Navbar",
        props: ["logo", "alt"]
    }
</script>


<!--STYLE---------------------------------------------------------->
<style scoped>

    #navBar{

       background-color: #242425; 
       border-bottom: 4px #000000 solid;
       padding: 15px 50px;
       display: flex;
       justify-content: flex-start;
       align-items: center;
       height: 70px;

    }

    #navBar #logoURL{

        vertical-align: middle;
        margin-top: 20px;
        margin: auto;
        margin-left:  0;

    }

    

    #navBar #logoURL > *{

        vertical-align: middle;
        margin: auto;
        margin-left:  0;

        }

    #logo{

        width: auto;
        height: 40px;
    }

    #navBar a{

        text-decoration: none;
        margin: 10px;
        
    } 
    

    .botoes:hover{

        background-color: #efa335;
        color: black;
        transition: .3s;

    }

    .botoes {
        padding: 8px;
        border-radius: 30px;
        background-color: #000000;
        color: #efa335;
        border: 1px #efa335 solid;
    }

     .botoes:active {
            background-color: rgb(218, 87, 0);
            color: #000000;
            transition: 0.1s;
     }

    #divisoria{

        color: #efa335;

    }

    #nomeNav {
        font-weight: bold;
        font-family: Arial, Helvetica, sans-serif;
        color: #efa335;
    }

</style>

