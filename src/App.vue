<script setup>
import {ref} from "vue";
//variável com tarefas
const tarefas = ref([
  "Estudar Vue.js 0",
  "Entregar currículo 1",
  "Treinar 2",
  "Limpar a varanda 3"
])

//função para remover:
function removerTarefa(index) {
  tarefas.value.splice(index, 1)
}

//variavel para nova tarefa
const novaTarefa = ref("");
//função de adicionar:
function adicionarTarefa() {
  if(novaTarefa.value.trim() !==""){
    tarefas.value.push(novaTarefa.value.trim())
    novaTarefa.value = ""
  }
}
</script>

<template>
  <h1>📝Lista de Tarefas</h1>
  <div v-if="tarefas.length === 0">
    <!--template não usamos .value pra variaveis reativas, apenas no script-->
    <p>Parabéns! Você é top!</p>
  </div>
  <ul v-else>
    <!--v-for é loop estamos usando para renderizar caa elemento-->
    <li v-for="(tarefa, index) in tarefas" :key="index">{{ tarefa }} <button @click="removerTarefa">❌ Remover</button></li>
  </ul>
  <section>
    <input type="text" placeholder="Digite sua nova tarefa" v-model="novaTarefa">
    <button @click="adicionarTarefa">Adicionar</button>
  </section>
</template>