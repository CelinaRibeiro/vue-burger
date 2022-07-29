<template>
    <div id="main-banner">
        <h1>Order Your Burger</h1>
    </div>
</template>

<script>
    export default {
        name: "Banner"
    }
</script>

<style scoped>
    #main-banner {
        background-image: url('/public/img/burger1.jpg');
        background-position: 0, 250px;
        background-size: cover;
        height:500px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }
    #main-banner h1 {
        width: 100vw;
        color: #fff;
        text-align: center;
        font-size: 55px;
        display: flex;
        justify-content: center;
    }

</style>