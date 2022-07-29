<template>
    <div id="footer">
        <p>VUE Burger &copy; 2022</p>
    </div>
</template>

<script>
    export default {
       name: "Footer"
    }
</script>

<style scope>
    #footer {
        height: 200px;
        background-color: #222;
        border-top: 4px solid #111;
        color: #fcba03;
        display: flex;
        align-items: center;
        justify-content: center;
        bottom: 0;
        width: 100%;
    }
</style>