<script setup lang="ts">
import {ref} from "vue";

const initialDate = new Date(Date.now());
const initialTargetDate = new Date(initialDate.getFullYear() + 1, 0, 1);
const initialTimeDifference = (initialTargetDate.getTime() / 1000 - initialDate.getTime() / 1000).toFixed(0).toString();

let timeDifference = ref<string>(initialTimeDifference);
const refreshIntervalInMs = 1000;

const countTimeDifference = () => {
  const currentDate = new Date(Date.now());
  const targetDate = new Date(currentDate.getFullYear() + 1, 0, 1);

  const difference = targetDate.getTime() / 1000 - currentDate.getTime() / 1000;
  timeDifference.value = difference.toFixed(0);
}

setInterval(countTimeDifference, refreshIntervalInMs)

</script>

<template>
  <div>
    <h1
    >{{ Number(timeDifference) <= 0 ? 'Happy New Year!' : timeDifference }}</h1>
  </div>
</template>

<style scoped>
div {
  display: flex;
  flex-direction: row;
  word-break: break-word;
  flex-wrap: wrap;
}

h1 {
  display: flex;
  flex-direction: row;
  margin: 0;

  font-size: 10rem;
  font-weight: bolder;
  filter: drop-shadow(0 0 0.6rem rgba(0, 0, 0, 0.45));

  transition: 0.4s;

  animation: glowHeading;
  animation-duration: 1s;
  animation-iteration-count: infinite;
}

@keyframes glowHeading {
  0% {
    transform: scale(1.028);
    filter: drop-shadow(0 0 .8rem rgba(113, 196, 25, 0.61));
    color: #dfffe1;
  }
  12% {
    filter: drop-shadow(0 0 .8rem rgba(108, 180, 32, 0.63));
  }
  100% {
    color: #ffffff;
  }
}

@media screen and (max-width: 1050px) {
  h1 {
    font-size: 8rem;
  }
}

@media screen and (max-width: 600px) {
  h1 {
    font-size: 3rem;
  }
}
</style>
