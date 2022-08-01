<template>
    <div class="message-container">
       <p> {{ msg }}</p>
    </div>
</template>

<script>
    export default {
        name: "Message",
        props: {
            msg: String
        }
    }
</script>

<style scoped>
.message-container {
    color: #454585;
    background-color: #cce5ff;
    border: 1px solid #ddd;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
   
}
</style>