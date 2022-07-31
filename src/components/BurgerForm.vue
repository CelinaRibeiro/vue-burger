<template>
    <div>
        <p>Componente de mensagem</p>
        <div>
            <form id="burger-form" @submit="createBurger">
                <div class="input-container">
                    <label for="nome">Seu nome:</label>
                    <input type="text" name="nome" id="nome" v-model="nome" >
                </div>

                 <div class="input-container">
                    <label for="pao">Pão:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">-- Selecione --</option>
                         <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                            {{ pao.tipo }}
                         </option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Tipo de carne:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option>-- Selecione --</option>
                         <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                            {{ carne.tipo }}
                         </option>
                    </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="opcionais">Opcionais:</label>
                   <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id" >
                        <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span>{{ opcional.tipo }}</span>
                   </div>
                </div>

                <div class="input-container">
                    <input type="submit" value="Comprar" class="submit-btn">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "BurgerForm",
        data() {
            return {
                //dados que vem de servidor
                paes: null,
                carnes: null,
                opcionaisdata: null,
                //dados que vão pro servidor
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                msg: null
            }
        },
        methods: {
            async getIngredientes() {
                const req = await fetch("http://localhost:3000/ingredientes");
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            },
             async createBurger(e) {
                e.preventDefault();

                const data = {
                    nome: this.nome,
                    carne: this.carne,
                    pao: this.pao,
                    opcionais: Array.from(this.opcionais),
                    status: "Solicitado"
                }

                const dataJson = JSON.stringify(data);

                const req = await fetch("http://localhost:3000/burgers", {
                    method: "POST",
                    headers: { "Content-Type": "application/json"},
                    body: dataJson
                });

                const res = await req.json();

                //limpar os campos 
                this.nome = "";
                this.carne = "";
                this.pao = "";
                this.opcionais = "";
            }
        },
        mounted() {
            this.getIngredientes()
        },
    }
</script>

<style scoped>
    #burger-form {
        max-width: 400px;
        margin: 0 auto;   
    }
    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
        
    }
    label {
        font-weight: bold;
        margin-bottom: 12px;
        color: #454545;
        padding: 5px;
    }
    input, select {
        padding: 12px 10px;
        border-radius: 5px;
        width: 400px;
        border: 1px solid #454545;
    }
    #opcionais-container {
        flex-direction: row;
        flex-wrap: wrap;
    }
    #opcionais-title {
        width: 100%;
    }
    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 15px;
    }
    .checkbox-container span,
    .checkbox-container input {
        width: auto;
    }
    .checkbox-container span {
        margin-left: 6px;
    }
    .submit-btn {
        background-color: #E49524;
        color: #fff;
        font-weight: 700;
        border: 1px solid #cdcdcd;
        border-radius: 5px;
        padding: 15px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
        text-transform: uppercase;
    }
    .submit-btn:hover {
        background-color: #daac6c;
        color: #ddd;
    } 

</style>