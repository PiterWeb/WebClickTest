<script setup>

defineProps({
    count: {
        type: Number,
        default: 0
    },
    onClick: {
        type: Function,
        default: function () {}
    }
});

</script>

<template>

    <button type="button" @click="onClick"><span v-if="count > 0">Click</span> <span v-else>Start</span></button>

</template>

<style scoped>

    button {

        background-color: #e74c3c;
        color: #fff;
        padding: 1rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        margin-bottom: 1rem;
        font-size: 1.2rem;
        font-weight: bold;
        width: 75%;
        height: 75%;
        position: relative;
        box-sizing: border-box;
        box-shadow: 0 0 0 1px rgb(58, 27, 27);

    }

    button:hover {

        background-color: #c0392b;
        color: #fff;

    }

    button:active {

        background-color: #c0392b;
        color: #fff;
        transform: translateY(2px);

    }

</style>