<!-- 1 -->


<template><!--TEMPLATE---------------------------------------------->
    
    <div>   

        <componenteMensagem :msg="msg" v-show="msg"/>

        <div class="main-container">

            <table id="burguer-table">

                <!--CABEÇALHO DA TABELA ----------------------> 

                <thead id="burguer-table-heading">
                    <tr>
                        
                        <th class="order-id">ID</th>
                        <th>CLIENTE:</th>
                        <th>PÃO:</th>
                        <th>CARNE:</th>
                        <th>OPCIONAIS:</th>
                        <th>STATUS:</th>
                        <th></th>

                    </tr>


                </thead>


            <!--INFORMAÇÕES DA TABELA ---------------------->

                <tbody id="burguer-table-rows">

                    <tr class="burguer-row" v-for="burguer in burguers" :key="burguer.id">



                        <td class="order-number">{{ burguer.id }}</td>

                        <td>{{ burguer.nome }}</td>

                        <td>{{burguer.pao}}</td>

                        <td>{{ burguer.carne }}</td>

                        <td name="opcionais">

                            <ul>

                                <li v-for="(opcional, index) in burguer.opcionais" :key="index">
                            
                                    • {{ opcional }}

                                </li>

                            </ul>

                        </td>


                        <!--SELETOR DE STATUS DO PEDIDO ---------------------->

                        <td>

                            <Select name="status" class="status" @change="updateBurguer($event, burguer.id)">

                                <option>Selecione:</option>
                                <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burguer.status == s.tipo">
                                    {{s.tipo}}
                                </option>
                        
                            </Select>

                        </td>


                        <!--Botão de excluir ---------------------->
                        <td>

                            <button class="delete-btn" @click="deleteBurguer(burguer.id)"></button>

                        </td>


                    </tr>

                </tbody>

            </table>

        </div>
    </div>
</template>

<!--=============================================================-->


<!-- 2 -->


<!--SCRIPT--------------------------------------------------------->
<script>

    import componenteMensagem from '../components/componenteMensagem.vue';

    export default {

         data(){

          return{

            burguers:null,
            burguers_id: null,
            status:[],
            msg: null,

          }

        },

        components:{

            componenteMensagem,

        },

        methods:{

            async getPedidos(){

                const req = await fetch("http://localhost:3000/burgers");

                const data = await req.json();

                this.burguers = data;

                //resgatar os status
                this.getStatus();

             },

            async getStatus(){

                const req = await fetch("http://localhost:3000/status");

                const data = await req.json();

                this.status = data;

            },

            async deleteBurguer(id){

                const req = await fetch(`http://localhost:3000/burgers/${id}`, {

                    method: "DELETE"
                });

                const res = await req.json();

                //msg
                    this.msg = `PEDIDO Nº ${res.id} REMOVIDO COM SUCESSO!`;
                    //limpar mensagem
                    setTimeout(() => this.msg = "", 4000);

                    
                this.getPedidos();

            },

            async updateBurguer(event, id)  {

                const option = event.target.value;

                const dataJson = JSON.stringify({status: option});

                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                
                    method: "PATCH",
                    headers: {"Content-Type": "application/json"},
                    body: dataJson
                });

                const res = await req.json();

                    //MENSAGEM  
                    this.msg = `PEDIDO Nº ${res.id} ATUALIZADO PARA: ${res.status}`;
                    //limpar mensagem
                    setTimeout(() => this.msg = "", 4000);

            },

        },

          mounted(){

            this.getPedidos();

          },
      
    }

</script>

<!--=============================================================-->


<!-- 3 -->


<!--STYLE---------------------------------------------------------->
<style scoped>

    *{
        list-style-type:none;
  
    }

    .main-container{

        min-width: 900px;
        margin: 0 auto;
        border: 2px #efa335 solid;
        border-radius: 2em;
        overflow: hidden;

    }

    table{

        width: 100% ;
        border-collapse: collapse;
        margin: 0 auto;
        background-color: rgb(58, 58, 58);
        text-align: center;
        
    }

    #burguer-table-heading th{

        background-color: rgb(36, 36, 36);
        font-weight: bold;
        padding: 20px;
        Color: #efa335;
        border-right: 1px solid #efa335;  
         

    }

    .burguer-row{
        color: #ffffff;

    }

    .burguer-row td{

        padding: 30px;
        border-bottom: 1px solid #efa335;
        border-top: 1px solid #efa335;         
        
    }

    #burguer-table-heading .order-id,
    .burguer-row .order-number{

      width: 5%;  

    }


    select{

        padding: 12px 6px;
        background-color:rgb(58, 58, 58);
        color: white;
        border-radius: 20px;
        
    }

    .delete-btn{
        background-image: url("/public/img/X-icon.png");;
        background-repeat: no-repeat;
        padding: 15px;
        cursor: pointer;
        border-radius: 50%;
        margin-top: 10px;
        width: auto;
        background-size: contain;
        background-color: #790000;
        box-shadow: 0 4px #500000;
        border: #500000;
        width: 0 auto;
        vertical-align: middle;
    }

    .delete-btn:active{

        box-shadow: 0 1px #500000;
        transform: translateY(3px);

    }




</style>

<!--=============================================================-->