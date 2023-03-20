

<!-- 1 -->


<template><!--TEMPLATE---------------------------------------------->
    
    <div>

        <div class="SubmiteMessage-container">

            <p>{{ msg }}</p>

        </div>

    </div>

</template>

<!--=============================================================-->


<!-- 2 -->


<!--SCRIPT--------------------------------------------------------->
<script>

    export default {

        name: "mensagem",
        props:{

            msg: String,

        }

    }
</script>

<!--=============================================================-->


<!-- 3 -->


<!--STYLE---------------------------------------------------------->
<style scoped>

    .SubmiteMessage-container{

        margin: 30px auto;
        align-items: center;
        background-color: rgb(54, 255, 54);
        max-width: 400px;
        padding: 30px;
        border-radius: 20px;
        color: rgb(15, 95, 15);
        font-size: 15px;
        font-weight: bold;
        text-align: center;
        
    }

</style>

<!--=============================================================-->