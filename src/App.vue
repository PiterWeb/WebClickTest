<script setup>

import { ref, watch } from 'vue';

import LabelVue from './components/label.vue';
import AlertVue from './components/alert.vue';
import ClickButtonVue from './components/clickButton.vue';

const maxTime = 10;

const count = ref(0)
const testOn = ref(false)
const time = ref(maxTime)

function increment () {
  count.value += 1;
}

function resetCount () {
  testOn.value = false;
  time.value = maxTime;
  alert(`You have clicked ${count.value} times in 10 seconds`);
  count.value = 0;
}

function startTimer () {
  testOn.value = true;
  setInterval(() => {
    if (testOn.value) {
      time.value--;
    }
  }, 1000);
}

watch(count , async (newCount , oldCount) => {

  if (oldCount === 0) {
    startTimer();
    await new Promise(resolve => setTimeout(resolve, 10000));
    resetCount();
  }

})

</script>

<template>

  <h3>10 seconds click test</h3>

  <LabelVue :count="count"></LabelVue>

  <AlertVue :count="count"></AlertVue>

  <ClickButtonVue :count="count" :onClick="increment"></ClickButtonVue>

  <p>Time left: {{time}}</p>

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
