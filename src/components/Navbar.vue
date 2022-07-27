<template>
    <div id="nav">
       <router-link to="/"><img src="" id="logo"></router-link>
       <router-link class="home" to="/">Home</router-link>
       <router-link to="/pedidos">Pedidos</router-link>
    </div>
</template>

<script>
    export default {
        name: "Navbar"
    }
</script>

<style scoped>
    .home {
        margin-right: 20px;
    }
</style>