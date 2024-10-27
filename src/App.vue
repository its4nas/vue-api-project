<script setup>
  import confetti from 'canvas-confetti';
  import { ref } from 'vue';

  const data = ref(null);
  const OFFICE_API = "https://rickandmortyapi.com/api/character/";

  fetch(OFFICE_API).then((d) => d.json())
  .then((message) => {
    data.value = message.results;
  })

  function showconfetti() {
    confetti.create(document.getElementById('canvas'), {
      resize: true,
      useWorker: true,
    })({ particleCount: 200, spread: 200 });
  }

  
</script>

<template>

<div dir="rtl">
  <table>
    <tr>
        <th></th>
        <th>08:00 - 10:00</th>
        <th>10:00 - 12:00</th>
        <th>12:00 - 14:00</th>
        <th>14:00 - 16:00</th>
        <th>16:00 - 18:00</th>
    </tr>
    <tr>
        <th>السبت</th>
        <td>Data 1-1</td>
        <td>Data 1-2</td>
        <td>Data 1-3</td>
        <td>Data 1-4</td>
        <td>Data 1-5</td>
    </tr>
    <tr>
        <th>الأحد</th>
        <td>Data 2-1</td>
        <td>Data 2-2</td>
        <td>Data 2-3</td>
        <td>Data 2-4</td>
        <td>Data 2-5</td>
    </tr>
    <tr>
        <th>الإثنين</th>
        <td>Data 3-1</td>
        <td>Data 3-2</td>
        <td>Data 3-3</td>
        <td>Data 3-4</td>
        <td>Data 3-5</td>
    </tr>
    <tr>
        <th>الثلاثاء</th>
        <td>Data 4-1</td>
        <td>Data 4-2</td>
        <td>Data 4-3</td>
        <td>Data 4-4</td>
        <td>Data 4-5</td>
    </tr>
    <tr>
        <th>الأربعاء</th>
        <td>Data 5-1</td>
        <td>Data 5-2</td>
        <td>Data 5-3</td>
        <td>Data 5-4</td>
        <td>Data 5-5</td>
    </tr>
    <tr>
        <th>الخميس</th>
        <td>Data 6-1</td>
        <td>Data 6-2</td>
        <td>Data 6-3</td>
        <td>Data 6-4</td>
        <td>Data 6-5</td>
    </tr>
</table>

</div>
  <div>
      <h1>Characters</h1>
      <div>
        <div class="content-characters" v-if="data">
            <div class="content-characters" 
            v-for="character in data" 
            :key="character.id">
        <div class="character">
          <img :src="character.image" alt="">
        <div class="info-character">
          <h2> {{ character.name}}</h2>
          <h4> {{ character.species}}</h4>
          <h4> {{ character.status}}</h4>
        </div>
        </div>
      </div>
    </div>
    </div>
   </div>

  <button @click="showconfetti">Click me</button>
</template>

<style scoped>
table {
    width: 100%;
    border-collapse: collapse;
}

th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
}
.content-characters {
  background: #002128;
  padding: 1rem;
  border-radius: 1rem;
}
.content-characters:hover {
  background: #1b1b1b;
}
.character {
  display: flex;
  justify-content: center;
  align-items: center;
}
.info-character {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 0 auto;
}
img.logo {
  width: 70%;
}
img {
  height: 50%;
  width: 50%;
  border-radius: 1rem;
}
h1 {
  color: #00ff97;
}
h2 {
  font-weight: bold;
  font-size: 1.2rem;
  padding: 1rem;
  background: #00ff97;
  border-radius: 0.8rem;
  margin: 1rem;
}
h4 {
  margin: 1rem;
  color: #ffffff;
  background: #8b8b8b;
  border-radius: 0.4rem;
  font-weight: inherit;
  padding: 0.2rem;
}
input{
  text-align: center;
  background: #002128;
  outline: none;
  border: 0;
  width: 300px;
  margin: 1rem;
  padding: 1rem;
  color: white;
  font-weight: 700;
  border-radius: 1rem;
}
@media screen and (max-width: 918px) {
.content {
  grid-template-columns: 1fr 1fr;
}
.character {
  display: flex;
  align-items: center;
}
h2{
  font-size: 1rem;
}
}


@media screen and (max-width: 540px) {
.content {
  width: 90%;
  grid-template-columns: 1fr;
}
.character {
  display: flex;
  align-items: center;
}

}
</style>
