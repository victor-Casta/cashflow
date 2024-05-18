<template>
    <header>
        <img @click="reload" src="../assets/cash-flow-icon.svg" alt="logo">
        <h1>Cash<span>Flow</span></h1>
        <span></span>
    </header>
</template>

<script>
    export default {
        methods: {
            reload() {
                window.location.reload();
            }
        }
    }
</script>

<style>
    header {
        display: flex;
        justify-content: space-around;
        align-items: center;
        width: 100vw;
    }

    img,
    span {
        width: 48px;
    }

    h1 {
        font-size: 1.4rem;
        color: #529fdf;
    }

    h1 span {
        color: #76e7b8;
    }
</style>