

<!-- 1 -->


<template><!--TEMPLATE---------------------------------------------->

    <div>

        <!-- <p>Componente de mensagem</p><br><br> -->

        <div>

            <form id="burguer-form">


                <!--Nome do cliente -------------------->
                <div class="input-container">

                    <label for="nome">Nome do cliente: </label>
                    <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite seu nome">
                </div>


                <!--Tipo de Pão ------------------------>
                <div class="input-container">

                    <label for="pao">Escolha o tipo de pão: </label>
                    <select name="pao" id="pao" v-model="pao">

                        <option value="">Selecione o tipo de pão:</option>
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{pao.tipo}}</option>

                    </select>
                </div>


                <!--Tipo de Carne ------------------------>
                <div class="input-container">

                    <label for="carne">Escolha a carne do seu burguer: </label>
                    <select name="carne" id="carne" v-model="carne">

                        <option value="">Selecione o tipo de carne:</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>

                    </select>
                </div>


                <!--Acompanhamento ------------------------>
                <div id="opcionais-container" class="input-container">

                    <label id="opcionais-title" for="opcionais">Selecione os opicionais: </label>

                      <div v-for="opcional in opcionaisdata" :key="opcional.id" class="checkbox-container">
                            <input type="checkbox" :id="`op-${opcional.id}`" name="opcionais" v-model="opcionais" :value="opcional.tipo" />

                                <label :for="`op-${opcional.id}`">
                                    <span class="checkbox"></span>
                                    {{opcional.tipo}}
                                </label>

                        </div>
                </div>



                <!--Submite ----------------------------->

                <div class="input-container">

                    <input type="submit" class="submit-btn" value="ENVIAR PEDIDO">


                </div>
            </form>
        </div>
    </div>
</template>

<!--=============================================================-->


<!-- 2 -->


<!--SCRIPT--------------------------------------------------------->
<script>

    export default {

        name:"burguerForm",
        
        data() {
            return {

                paes: null,
                carnes: null,
                opcionaisdata: null,
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                status: "Solicitado",
                msg: null,

            }
        },

        methods:{

            async getIngredients(){

                const req = await fetch("http://localhost:3000/ingredientes");
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais


            }
        },

        mounted() {

            this.getIngredients()

        }

    }

</script>

<!--=============================================================-->


<!-- 3 -->


<!--STYLE---------------------------------------------------------->

<style scoped>

    #burguer-form{

        max-width: 400px;
        margin: 0 auto;
        padding-top: 50px;
        padding-bottom: 10px;
        padding-left: 50px;
        background-color: rgb(58, 58, 58);
        border-radius: 20px;
        color: white;

    }

    #burguer-form input[type=text], #burguer-form select {
        background-color: rgb(87, 87, 87);
        border-radius: 15px;
        border: 0;
        color: #ffffff;
        outline-style: none;
        opacity: .5;
        transition: .3s;
    }

    

    #burguer-form input[type=text]:focus, #burguer-form select:focus {
        opacity: 1;
    }


    .input-container{

        display: flex;
        flex-direction: column;
        margin-bottom: 50px;
    }


    label{

        font-weight: bold;
        margin-bottom: 15px;
        padding: 5px 10px;
        border-left: 4px solid #efa335;
    }


    input, select{

        padding: 5px 10px;
        width: 300px;
    }


    #opcionais-container{

        flex-direction: row;
        flex-wrap: wrap;
    }


    #opcionais-title{

        width: 100%;
    }


    .checkbox-container{

        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container > label {

        border-left: hidden;
    }


    .checkbox-container span,
    .checkbox-container input{

        width: auto;

    }


    .checkbox-container span{

        margin-left: 6px;
        font-weight: bold;
    }


    .submit-btn{

        font-weight: bold;
        padding: 15px;
        border-radius: 30px;
        background-color: 
            #efa335;
        color: black;
        border: 0;
        transition: all ease-in-out 0.2s;
        border-bottom: 4px #33333375 solid;
    }


    .submit-btn:hover{


        background-color: #ffa335;
        color: white;
        transition: 0.1s;
    }

        .submit-btn:active{


        background-color: #000000;
        color: white;
        transition: 0.3s;
        border-bottom: hidden;
    }





    input[type=checkbox] {
        display: none;
    }



    input[type=checkbox] + label > span {
        vertical-align: middle;
        margin-right: 8px ;

    }

    input[type=checkbox] + label > span.checkbox {
        display: inline-block;
        width: 30px;
        height: 30px;
        border: 1px #ffa335 solid;
        border-radius: 50%;

    }

    input[type=checkbox]:checked + label > span.checkbox {
        border: 3px #ffa335 solid;
        border-radius: 50;
        background-repeat: no-repeat;
        background-size: 15px;
        background-position: center;
        background-image: url("/public/favicon.ico");


    }



</style>

<!--=============================================================-->