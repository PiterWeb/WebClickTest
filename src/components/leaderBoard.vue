<script setup>

import { ref } from "vue";

const users = ref([{ name: "_", clicks: "_" }])

</script>

<template>

    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Clicks</th>
            </tr>
        </thead>
        <tbody>
            <tr class="user" v-for="(user, index) in users">
                <td>{{ user.name }}</td>
                <td>{{ user.clicks }}</td>
            </tr>
        </tbody>
    </table>

</template>

<style scoped>
template {
    width: 100%;
    height: 100%;
}

table {
    width: 50%;
    height: 100%;
    border-collapse: collapse;
    border: 1px solid black
}

thead {
    background-color: rgb(0, 0, 0);
    color: white;
}

.user {
    border: 1px 1px 1px 1px solid black;
}
</style>