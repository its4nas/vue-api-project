<script setup>
  import confetti from 'canvas-confetti';
  import { ref } from 'vue';

  const data = ref(null);
  const OFFICE_API = "https://rickandmortyapi.com/api";

  fetch(OFFICE_API).then((d) => d.json())
  .then((message) => {
    data.value = message;
  })

  function showconfetti() {
    confetti.create(document.getElementById('canvas'), {
      resize: true,
      useWorker: true,
    })({ particleCount: 200, spread: 200 });
  }

  
</script>

<template>
  <div v-if="data">
    <div v-for="item in data">
      <button @click="showconfetti">{{ item }}</button>
    </div>
  </div>
  <button @click="showconfetti">Click me</button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
