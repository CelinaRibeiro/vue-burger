<template>
    <div>
        <p>Componente de mensagem</p>
        <div>
            <form id="burger-form">
                <div class="input-container">
                    <label for="nome">Seu nome:</label>
                    <input type="text" name="nome" id="nome" v-model="nome" >
                </div>

                 <div class="input-container">
                    <label for="pao">Pão:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">-- Selecione --</option>
                         <option value="Integral">Integral</option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Tipo de carne:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">-- Selecione --</option>
                         <option value="Integral">Picanha</option>
                    </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="opcionais">Opcionais:</label>
                   <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="bacon" v-model="opcionais">
                        <span>Bacon</span>
                   </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="batata" v-model="opcionais">
                        <span>Batata</span>
                   </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="ovo" v-model="opcionais">
                        <span>Ovo</span>
                   </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="mussarela" v-model="opcionais">
                        <span>Mussarela</span>
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
        name: "BurgerForm"
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