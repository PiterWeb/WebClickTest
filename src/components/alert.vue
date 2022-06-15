<script setup>

    defineProps({
        count: {
            type: Number,
            default: 0
        }
    });

</script>

<template>

    <article class="alert">
        {{count}}
    </article>

</template>

<style scoped>

article {

    padding: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 1rem;
    background-color: #e0e0e0;
    color: #000;
    font-size: 1.2rem;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    position: relative;
    box-sizing: border-box;

}

</style>