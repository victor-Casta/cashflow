<template>
    <div class="header">
        <slot name="header"></slot>
    </div>
    <div class="resume">
        <slot name="resume"></slot>
    </div>
    <div class="movements">
        <div class="head" @click="showMovements = !showMovements" >
            <div class="grip"></div>
        </div>
        <div class="body" v-show="showMovements">
            <slot name="movements"></slot>
        </div>
        </div>
</template>

<script>
    export default {
        data() {
            return {
                showMovements: false
            }
        },
    }
</script>

<style scoped>
    .header,
    .resume,
    .movements {
        display: flex;
        justify-content: space-around;
        align-items: center;
        padding: 14px 0;
        box-sizing: border-box;
    }

    .header {
        position: fixed;
        width: 100vw;
    }

    .resume {
        min-height: 100vh;
    }

    .movements {
        z-index: 1;
        position: absolute;
        flex-direction: column;
        bottom: 0;
        width: 100vw;
        background-color: #31363F;
        box-shadow: 0 -8px 10px #b1dfe6;
        border-radius: 24px 24px 0 0;
    }

    .movements .head {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 24px;
        width: 100%;
        box-sizing: border-box;
        transition: all 0.5s ease-in-out;
    }

    .movements .body {
        height: 75vh;
        width: 100%;
    }

    .movements .head .grip {
        width: 120px;
        height: 8px;
        background-color: #e5e5e5;
        border-radius: 4px;
    }
</style>