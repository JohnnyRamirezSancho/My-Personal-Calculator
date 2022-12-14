<script setup>

import { ref, computed } from 'vue';

let textOnDisplay = "";
let showOnDisplay = ref(0);

const showDisplay = computed({
  get() {
    return showOnDisplay.value
  }
})

const addToDisplay = function (element) {
  if (element == "c") {
    showOnDisplay.value = 0;
    textOnDisplay = "";
    return
  }
  if (element == "=") {
    showOnDisplay.value = eval(showOnDisplay);
    textOnDisplay = textOnDisplay.value;
    return
  }

  textOnDisplay += element;
  showOnDisplay.value = showOnDisplay;
}

</script>

<template>
  <main>
    <p id="display">{{ showDisplay }}</p>
    <button id="oneKey" @click="addToDisplay(1)">1</button>
    <button id="twoKey" @click="addToDisplay(2)">2</button>
    <button id="additionKey" @click="addToDisplay(`+`)">+</button>
    <button id="subtractionKey" @click="addToDisplay(`-`)">-</button>
    <button id="multiplicationKey" @click="addToDisplay(`*`)">*</button>
    <button id="divisionKey" @click="addToDisplay(`/`)">/</button>
    <button id="equalKey" @click="addToDisplay(`=`)">=</button>
    <button id="resetKey" @click="addToDisplay(`c`)" class="resetButton">C</button>
  </main>
</template>

<style scoped>
p {
  color: white;
  font-size: 32px;
}

button {
  display: inline-block;
  width: 50px;
  height: 50px;
  border-radius: 5px;
  border: 1px solid black;
  font-size: 24px;
}

.resetButton {
  background-color: #ff0000;

}
</style>
