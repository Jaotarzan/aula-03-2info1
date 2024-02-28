<script setup>
import { ref, computed } from 'vue'

const contador1 = ref(0)
const contador2 = ref(0)
const booleano = ref(true)

function decrementar1() {
  if (contador1.value > 0) contador1.value--
}

function decrementar2() {
  if (contador2.value > 0) contador2.value--
}

const maiorMenor = computed(() => {
  return (contador1.value + contador2.value) > 10 ? true : false
})

const parImpar = computed(() => {
  return ((contador1.value + contador2.value) % 2 == 0) ? true : false
})

const VerdadeirFalso = computed(() => {
  return booleano.value ? "verdadeiro" : "falso"
})


</script>

<template>
<div class="contadores">
  <h1>contador1</h1>
  <p>contador: {{ contador1 }}</p>
  <button @click="contador1++">+</button>
  <button @click="decrementar1">-</button>
  <button @click="contador1=0">0</button>
</div>
<h1>+</h1>
<div class="contadores">
  <h1>contador2</h1>
  <p>contador: {{ contador2 }}</p>
  <button @click="contador2++">+</button>
  <button @click="decrementar2">-</button>
  <button @click="contador2=0">0</button>
</div>  
<h1>=</h1>
<div id="resultado">
  <h1>Resultado</h1>
  <p>resultado: {{ contador1 + contador2 }}</p>
  <div v-if="maiorMenor" id="maior">
    <p>O Valor é maior que 10</p>
  </div>
  <div v-else id="menor">
    <p>O valor é menor que 10</p>
</div>
<div v-if="parImpar" id="maior">
    <p>O Valor é Par</p>
  </div>
  <div v-else id="menor">
    <p>O valor é Impar</p>
</div>
<div>
  <p>{{ VerdadeirFalso }}</p>
  <button @click="booleano = !booleano">Inverter</button>
</div>
</div>
</template>

<style scoped>

* {
  margin: none;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
.contadores, #resultado {
  background-color: rgba(197, 183, 183, 0.712);
  color: rgb(0, 0, 0);
  border-radius: 10px;
  margin: 5%;
  text-align: center;
}

h1 {
  text-align: center;
}

button {
  background-color: black;
  color: white;
  border: none;
}

#maior {
  background-color: green;
}

#menor {
  background-color: red;
}
</style>
