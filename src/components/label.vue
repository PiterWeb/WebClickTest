<script setup>

import { inject } from 'vue';

const count = inject('count');

</script>

<template>


  <p v-if="count >= 80">You are awesome! MORE THAN 80 CLICKS</p>
  <p v-else-if="count >= 50">You are GREAT, 50 clicks</p>
  <p v-else-if="count >= 35">LET'S GO 35 CLICKS</p>
  <p v-else-if="count >= 20">NICE 20 Clicks</p>
  <p v-else-if="count >= 10">It seems that you have reached 10 clicks</p>
  <p v-else-if="count >= 5">EASY, you have reached 5 clicks</p>
  <p v-else>GET READY</p>


</template>

<style scoped>

  p {
    font-size: 1.5rem;
    font-weight: bold;
    color: #000000;
    text-align: center;
    margin-top: 1rem;
  }

</style>