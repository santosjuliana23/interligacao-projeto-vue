<script setup>
import { ref } from 'vue'

const perfilSalvo = ref(false)
const nome = ref('')
const email = ref('')
const senha = ref('')
const datanasc = ref('')
const estado = ref('')
const cidade = ref('')
const endereco = ref('')
const linguagemdeprog = ref('')
const hobbies = ref('')
const biografia = ref('')
const estados = {
  AC: 'Acre',
  AL: 'Alagoas',
  AP: 'Amapá',
  AM: 'Amazonas',
  BA: 'Bahia',
  CE: 'Ceará',
  DF: 'Distrito Federal',
  ES: 'Espírito Santo',
  GO: 'Goiás',
  MA: 'Maranhão',
  MT: 'Mato Grosso',
  MS: 'Mato Grosso do Sul',
  MG: 'Minas Gerais',
  PA: 'Pará',
  PB: 'Paraíba',
  PR: 'Paraná',
  PE: 'Pernambuco',
  PI: 'Piauí',
  RJ: 'Rio de Janeiro',
  RN: 'Rio Grande do Norte',
  RS: 'Rio Grande do Sul',
  RO: 'Rondônia',
  RR: 'Roraima',
  SC: 'Santa Catarina',
  SP: 'São Paulo',
  SE: 'Sergipe',
  TO: 'Tocantins'
}
const editarPerfil = () => {
  perfilSalvo.value = true
}
</script>

<template>
  <form @submit.prevent="editarPerfil">
    <div id="teste">
      <p>Insira seu nome:</p>
      <input type="text" v-model="nome" maxlength="20" minlength="3" />
      <p>Insira seu email:</p>
      <input type="email" v-model="email" maxlength="20" minlength="3" />
      <p>Insira sua senha:</p>
      <input type="password" v-model="senha" />
      <p>Confirme sua senha:</p>
      <input type="password" v-model="senha" />
      <p>Insira sua data de nascimento: {{ datanasc }}</p>
      <input type="date" v-model="datanasc" />
      <p>Insira seu endereço:</p>
      <input type="text" v-model="endereco" />
      <p>Insira sua cidade:</p>
      <input type="text" v-model="cidade" />
      <p>Insira seu estado:</p>
      <select v-model="estado">
        <option value="">Selecionar Estado</option>
        <option v-for="(value, key) in estados" :key="key" :value="key">{{ value }}</option>
      </select>
      <p>Insira seus hobbies:</p>
      <input type="text" v-model="hobbies" />
      <p>Insira sua linguagem de programação:</p>
      <input type="text" v-model="linguagemdeprog" />
      <p>Insira sua biografia:</p>
      <input type="text" v-model="biografia" />

      <br />
      <button @click="editarPerfil" type="submit" id="editar">Editar perfil</button>
    </div>
  </form>
  <div class="perfilsalvo" v-if="perfilSalvo">
    <h2>Informações do Perfil:</h2>
    <p>Nome: {{ nome }}</p>
    <p>Email: {{ email }}</p>
    <p>Data de Nascimento: {{ datanasc }}</p>
    <p>Endereço: {{ endereco }}</p>
    <p>Cidade: {{ cidade }}</p>
    <p>Estado: {{ estados[estado] }}</p>
    <p>Hobbies: {{ hobbies }}</p>
    <p>Linguagem de Programação: {{ linguagemdeprog }}</p>
    <p>Biografia: {{ biografia }}</p>
  </div>
</template>

<style scoped>
#editar {
  width: 100px;
  height: 20px;
  border-radius: 5px;
  border: 2px solid black;
  background-color: rgb(245, 185, 196);
  letter-spacing: 1px;
  justify-content: center;
}
.perfilsalvo {
  color: rgb(0, 0, 0);
  border-radius: 5px;
  margin-left: 300px;
  margin-bottom: 250px;
  width: 450px;
}
#teste {
  color: rgb(0, 0, 0);
  text-align: left;
  width: 450px;
  display: flex;
  flex-direction: column;
}
</style>
