<template>
    <div class="green">
        {{msg}}
    </div>
</template>

<script>
    export default {
        props: {
            msg: String
        }
    }
</script>

<style scoped>
    .green{
        width: 400px;
        height: 200px;
        background-color: #af8;
        padding: 30px;
        box-sizing: border-box;
        font-style: 18;
        font-weight: bold;
    }
</style>