<script setup>

import { ref, watch, provide } from 'vue';

import LabelVue from './components/label.vue';
import AlertVue from './components/alert.vue';
import ClickButtonVue from './components/clickButton.vue';
import LeaderBoard from './components/leaderBoard.vue';
import Swal from 'sweetalert2';
import 'sweetalert2/dist/sweetalert2.min.css';

const maxTime = 10; // max time in seconds

const count = ref(0) // number of clicks
const testOn = ref(false) // test is running
const time = ref(maxTime) // seconds

function increment() {
  count.value += 1;
}

provide('count', count)

setInterval(() => {
  if (testOn.value && time.value > 1) {
    return time.value--;
  }

  if (testOn.value && time.value > 0) {
    time.value = 0;
    setTimeout(() => {
      Swal.fire({
        title: 'Score',
        text: ` ${count.value} clicks in ${maxTime} seconds`,
        showCancelButton: false,
        confirmButtonColor: '#d33',
        confirmButtonText: 'Try again',
        icon:'success',
        allowOutsideClick: false,
      })
      // alert(`You have clicked ${count.value} times in ${maxTime} seconds`);
      count.value = 0;
    }, 100)
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

  <h1>10s Click Test</h1>

  <main>

    <section id="test">

      <LabelVue :count="count"></LabelVue>

      <AlertVue :count="count"></AlertVue>

      <ClickButtonVue :onClick="increment"></ClickButtonVue>

      <div v-if="testOn === true" id="timeSection">
        <p id="time">{{ time }}</p>
      </div>

    </section>
    <section>

    </section>

    <section id="leaderBoard">

      <LeaderBoard />

    </section>

  </main>

</template>

<style scoped>
main {
  display: grid;
  align-items: baseline;
  justify-items: stretch;
  grid-template-columns: 60% auto auto;
}

#test {
  padding: 3rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#timeSection {
  /* modern light box */
  background-color: #ffffff;
  color: rgb(255, 255, 255);
  font-size: 1.2rem;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 4rem;
  height: 4rem;
  border: 0.25rem dashed black;
  box-sizing: border-box;

}

#time {
  /* counter animation */
  animation: counter-animation 1s steps(10, end) infinite;
  animation-direction: alternate;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  font-size: 2rem;
  font-weight: bold;
  color: #e74c3c;
  text-align: center;

}

@keyframes counter-animation {
  0% {
    opacity: 50%;
  }

  100% {
    opacity: 100%;
  }
}
</style>
