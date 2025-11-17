<script setup lang="ts">
import {ref, computed} from 'vue'
const peso = ref <number> (null as unknown as number)
const altura = ref <number> (null as unknown as number)
const IMC = computed(()=>{
  return peso.value/(altura.value **2)
})
</script>

<template>
  <div class="container">
    <div><label for="peso">Peso: </label></div>
    <div><input v-model="peso" type="number" min="1" id="peso" step="0.01"></input></div>
    <div><label for="altura">Altura: </label></div>
    <div><input v-model="altura" type="number" min="1" id="altura" step="0.01"></input></div>
    <div>
      <div v-if="altura > 0 && peso > 0">
        <h3 v-if="IMC < 18.5 && IMC">Abaixo do peso</h3>
        <h3 v-else-if="IMC >= 18.5 && IMC < 25">Peso normal</h3>
        <h3 v-else-if="IMC >= 15 && IMC < 30">Sobrepeso</h3>
        <h3 v-else>Obesidade</h3>
        <h3>IMC: {{ IMC.toFixed(2) }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
