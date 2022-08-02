<template>
   <div id="burger-table">
        <div>
            <div id="burger-table-heading">
                <div class="order-id">#</div>
                <div>Cliente</div>
                <div>Pão</div>
                <div>Carne</div>
                <div>Opcionais</div>
                <div>Ações</div>
            </div>
        </div>
        <div id="burger-table-rows">
            <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                <div class="order-number">{{ burger.id }}</div>
                <div>{{ burger.nome }}</div>
                <div>{{ burger.pao }}</div>
                <div>{{ burger.carne }}</div>
                <div>
                    <ul>
                        <li v-for="(opcional, index) in burger.opcionais" :key="index">
                            {{ opcional }}
                        </li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option class="status" value="">Selecione</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>
        </div>
   </div>
</template>

<script>
import { throwStatement } from '@babel/types';

   export default {
        name: 'Dashboard',
        data() {
            return {
                burgers: null,
                burger_id: null,
                status: []
            }
        },
        methods: {
            async getPedidos() {
                const req = await fetch("http://localhost:3000/burgers");

                const data = await req.json();

                this.burgers = data;

                //resgatar os status
            }
        },
        mounted() {
            this.getPedidos();
        }
   }
</script>

<style scoped>
    #burger-table {
        max-width: 1200px;
        margin: 0 auto;
    }
    #burger-table-heading,
    #burger-table-rows,
    .burger-table-row {
        display: flex;
        flex-wrap: wrap;
    }
    #burger-table-heading {
        font-weight: 300;
        padding: 12px;
        border-bottom: 1px solid #454545;
    }
      #burger-table-heading div,
      .burger-table-row div {
        width: 19%;
    }
    .burger-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #ddd;
    }
     #burger-table-heading .order-id,
     .burger-table-row .order-number {
        width: 5%;
    }
    select {
        padding: 6px 6px;
        margin-right: 12px;
    }
    .delete-btn {
        background-color: #E49524;
        color: #fff;
        font-weight: 500;
        border: 1px solid #fff;
        padding: 9px 20px;
        margin: 0 auto;
        border-radius: 3px;
        cursor: pointer;
        transition: .5s;
        font-size: 12px;
    }
    .delete-btn:hover {
        color: #fff; 
        background-color: #e9a74a;
    }


</style>