<script setup>
import { ref } from 'vue'

const random = ['ค้อน', 'กระดาษ', 'กรรไกร', 'ความรัก'];
const botRandom = ref('');
const playerRandom = ref('');
const botScore = ref(0);
const playerScore = ref(0);

function RandomImg(pic) {
  const allImgs = {
    'ค้อน': './assets/3.jpg',
    'กระดาษ': './assets/1.jpg',
    'กรรไกร': './assets/2.jpg',
    'ความรัก': './assets/4.png',
  };

  return allImgs[pic];
}

function playButton() {
  botRandom.value = random[Math.floor(Math.random() * random.length)];
  playerRandom.value = random[Math.floor(Math.random() * random.length)]

  if (
    (botRandom.value === 'ค้อน' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'กระดาษ' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'กรรไกร' && playerRandom.value === 'กระดาษ') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กระดาษ')
  ) {
    botScore.value++;
  } else {
    playerScore.value++;
  }
}

function resetGame() {
  botRandom.value = '';
  playerRandom.value = '';
  botScore.value = 0;
  playerScore.value = 0;
}
</script>
<template>
<div>
  <div class="play1111">
    <div>
      <h2 class="bot1">play</h2>
  <div>
  <img v-if="playerRandom === 'ค้อน'" src="./assets/3.jpg" alt="ค้อน" />
  <img v-if="playerRandom === 'กระดาษ'" src="./assets/1.jpg" alt="กระดาษ" />
  <img v-if="playerRandom === 'กรรไกร'" src="./assets/2.jpg" alt="กรรไกร" />
  <img v-if="playerRandom === 'ความรัก'" src="./assets/4.png" alt="ความรัก" />
</div>
<div>
  <h3 style="color: red;">ผู้เล่น1</h3>{{ gameResult1 }}
</div>
</div>
  </div>
</div>

  <div class="play222">
    <div>
      <h2 class="play">bot</h2>
  <div>
  <img v-if="botRandom === 'ค้อน'" src="./assets/3.jpg" alt="ค้อน" />
  <img v-if="botRandom === 'กระดาษ'" src="./assets/1.jpg" alt="กระดาษ" />
  <img v-if="botRandom === 'กรรไกร'" src="./assets/2.jpg" alt="กรรไกร" />
  <img v-if="botRandom === 'ความรัก'" src="./assets/4.png" alt="ความรัก" />
</div>
<div>
  <h3 style="color: rgb(69, 202, 255);">ผู้เล่น2</h3>
  {{ gameResult }}
</div>
</div>
</div>


<div class="text-score">
  <p style="color: rgb(242, 31, 196);">Point of Bot : &nbsp; {{ botScore }}</p>
  <p style="color: rgb(69, 202 255);"> Point of Player : &nbsp; {{ playerScore }}</p>
</div>
<button  @click="playButton" style="background-color: rgb(49, 212, 207);">Play</button> &nbsp;
<button  @click="resetGame" style="background-color: red;">Reset</button>
</template>

