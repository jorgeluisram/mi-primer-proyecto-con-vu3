
<script setup>
import {computed, ref}from 'vue'
const name = 'Vue dinamico'
const array = ref([])
//metodo
//ejercicio pi8ntar un contardor 3 botnoes aumentar disminuir y resetear
// cuando sea mayor pinte color verde cuando sea menor color rojo 
const counter = ref(0);
const increment = ()=>{
  
  counter.value ++;
  console.log(counter)
}
const disminuir = ()=>{counter.value --;}
const reset = ()=>{counter.value = 0;}
const agregar = ()=>{array.value.push(counter.value)}
const bloquearbtnAdd = computed(()=>{
  const numSearch = array.value.find(num => num === counter.value)
  if(numSearch === 0) return true // valida como booleando y no lo tomaria
  return numSearch ? true : false;//si existe retorne true si no false
})
</script>

<template>
  <div class="container text-center mt-3">

    <h2>Hola {{name.toUpperCase()}}</h2>
    <h2 :class=" counter > 0 ? 'positive' : 'negative'">{{counter}}</h2>
      <div class="btn-group">
        <button @click="increment" class="btn btn-success"> aumentar</button>
        <button @click="disminuir" class="btn btn-danger"> disminuir</button>
        <button @click="reset" class="btn btn-secundary"> reset</button>
        <button  @click="agregar" :disabled="bloquearbtnAdd" class="btn btn-primary"> add</button>
      </div>
    
      <ul class="list-group">
        <li
          class="list-group-item"
          v-for="(num,index) in array"
          :key="index">
          {{num}}
        </li>
      </ul>
  </div>
</template>

<style scoped>

.positive {
  color:green
}
.negative {
  color: red;
}
</style>