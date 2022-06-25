<script setup>

import { inject } from 'vue';

defineProps({
    onClick: {
        type: Function,
        default: function () { }
    }
});

const count = inject('count');

</script>

<template>

    <button type="button" @click="onClick"><span v-if="count > 0">Click</span> <span v-else>▶</span></button>

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
    box-shadow: 0px 1px 3px gray;
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