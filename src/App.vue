<script setup>
import {ref, computed} from "vue"
const counter = ref(0);
const favList = ref([]);
const disminuir = () => {
  counter.value--;
}
const aumentar = () => {
  counter.value++;
}
const reset = () => {
  counter.value = 0;
}
const add = () => {
  favList.value.push(counter.value);
}
const isDisabled = computed(()=>{
  return (favList.value.includes(counter.value));
})
</script>

<template>
  <h2 :class="{'red': counter<0, 'green': counter>0}" >{{ counter }}</h2>
  <button @click="aumentar">Aumentar</button>
  <button @click="disminuir">Disminuir</button>
  <button @click="reset">Resetear</button>
  <button @click="add" :disabled="isDisabled">Agregar</button>
  <ul v-if=favList.length>
    <li v-for="(item, index) in favList" :key="index">{{ item }}</li>
  </ul>
  <p v-else>No hay favoritos</p>
</template>

<style>
.red {
  color: red;
}
.green {
  color: green;
}
</style>
