<script setup lang="ts">
import {ref} from 'vue';
import Soma  from './components/soma.vue'
import subtrair from './components/subtrair.vue'
import Multiplicar from './components/Mult.vue'
import Dividir from './components/Divisao.vue'


let showSoma = ref(false);
let showSub = ref(false);
let showMult = ref(false);
let showDiv = ref(false);

//quando clicar em SOMA, todas as outras operações serao escondidas
//e somente a SOMA irá aparecer
function soma(){
  showSoma.value = true;
  showDiv.value = false;
  showMult.value = false;
  showSub.value = false;
}
function sub(){
  showSoma.value = false;
  showDiv.value = false;
  showMult.value = false;
  showSub.value = true;
}
function div(){
  showSoma.value = false;
  showDiv.value = true;
  showMult.value = false;
  showSub.value = false;
}
function mult(){
  showSoma.value = false;
  showDiv.value = false;
  showMult.value = true;
  showSub.value = false;
}


</script>

<template>
  <div class="container">

    <div class="cabecalho">
      <h1>Calculadora</h1>
      <p>Execute as quatro operações básicas</p>
    </div>

    <div class="card">
      <h2>Escolha a operação</h2>

      <div class="botoes">
        <button @click="soma">+</button>
        <button @click="sub">−</button>
        <button @click="mult">×</button>
        <button @click="div">/</button>
      </div>
    </div>

    <div class="card operacao">
      <Soma v-if="showSoma"/>
      <subtrair v-if="showSub"/>
      <Multiplicar v-if="showMult"/>
      <Dividir v-if="showDiv"/>
    </div>

  </div>
</template>

<style scoped>
body {
    margin: 0;
    background-color: #90a3f0 ;
    font-family: Arial, sans-serif;
}


.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 50px 30px;
  background-color: #90a3f0;
  min-height: 100vh;
}

.cabecalho {
  margin-bottom: 30px;
}

.cabecalho h1 {
  margin: 0;
  font-size: 42px;
  color: #17233c;
}

.cabecalho p {
  margin-top: 10px;
  color: #697386;
  font-size: 18px;
}


.card {
  background-color: white;
  padding: 30px;
  margin-bottom: 25px;

  border: 1px solid #e1e3e8;
  border-radius: 16px;

  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
}


.card h2 {
  margin: 0 0 20px;
  color: #17233c;
  font-size: 24px;
}


.botoes {
  display: flex;
  gap: 12px;
}

.botoes button {
  width: 60px;
  height: 55px;

  border: 1px solid #dcdfe6;
  border-radius: 10px;

  background-color: #ffffff;
  color: #17233c;

  font-size: 22px;
  font-weight: bold;

  cursor: pointer;

  transition: 0.2s;
}


.botoes button:hover {
  background-color: #5b4bea;
  border-color: #5b4bea;
  color: white;
  transform: translateY(-2px);
}


.operacao {
  min-height: 120px;
}
</style>