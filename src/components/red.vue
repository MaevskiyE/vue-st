<template>
    <div class="user_details">
        <div class="title">
            You may view the User Details here
        </div>
        Many details
        <p>user name: {{name}}</p>
    </div>
</template>

<style scoped>
    .user_details{
        width: 400px;
        height: 200px;
        background-color: #f55;
        display: flex;
        flex-direction: column;
        padding: 30px;
        box-sizing: border-box;
    }
    .title{
        font-size: 18px;
        font-weight: bold;
    }
</style>

<script>
    export default {
        props: {
            name: String
        }
    }
</script>