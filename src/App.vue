<script setup>

import { ref, watch } from 'vue';

import LabelVue from './components/label.vue';
import AlertVue from './components/alert.vue';
import ClickButtonVue from './components/clickButton.vue';

const maxTime = 10; // max time in seconds

const count = ref(0) // number of clicks
const testOn = ref(false) // test is running
const time = ref(maxTime) // seconds

function increment() {
  count.value += 1;
}


setInterval(() => {
  if (testOn.value && time.value > 1) {
    return time.value--;
  }

  if (testOn.value && time.value > 0) {
    time.value = 0;
    alert(`You have clicked ${count.value} times in ${maxTime} seconds`);
    count.value = 0;
  }

}, 1000)

watch(count, async (newCount, oldCount) => {

  if (newCount === 0) {
    testOn.value = false;
    time.value = maxTime;
    count.value = 0;
  }

  if (newCount > 0) {
    testOn.value = true;
  }

})

</script>

<template>

  <h3>10 seconds click test</h3>

  <LabelVue :count="count"></LabelVue>

  <AlertVue :count="count"></AlertVue>

  <ClickButtonVue :count="count" :onClick="increment"></ClickButtonVue>

  <p>Time left: {{ time }}</p>

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
