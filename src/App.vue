<script setup lang="ts">
import {ref} from "vue";

let timeDifference = ref<string>();
const refreshIntervalInMs = 100;

const countTimeDifference = () => {
  const currentDate = new Date(Date.now());
  const targetDate = new Date(2024, 0, 1);

  const difference = targetDate.getTime() / 1000 - currentDate.getTime() / 1000;
  timeDifference.value = difference.toFixed(0);
}

setInterval(countTimeDifference, refreshIntervalInMs)

</script>

<template>
  <div>
    <h1>{{ timeDifference }}</h1>
  </div>
</template>

<style scoped>
body {
  overflow: hidden;
}

h1 {
  font-size: 25rem;
  font-weight: bolder;
  filter: drop-shadow(0 0 0.6rem rgba(0, 0, 0, 0.45));
}

@media screen and (max-width:1050px) {
  h1 {
    font-size: 12rem;
  }
}

@media screen and (max-width:600px) {
  h1 {
    font-size: 7rem;
  }
}
</style>
