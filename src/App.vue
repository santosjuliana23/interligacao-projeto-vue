<script setup>
import { ref, reactive } from 'vue'

const usuario = reactive({
  nome: '',
  email: '',
  senha: '',
  datanasc: '',
  estado: '',
  cidade: '',
  endereco: '',
  linguagemdeprog: '',
  hobbies: '',
  biografia: '',
  estado: 'Informe seu estado',
})
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
const senha = ref('');
const perfilSalvo = ref(false)
const editarPerfil = () => {
  if(senha.value == usuario.senha && senha.value != '' ){
    perfilSalvo.value = !perfilSalvo.value
  }else{
    alert("senhas diferentes")
  }
}

</script>

<template>
  <div class="perfilsalvo" v-if="perfilSalvo">
    <h2>Informações do Perfil:</h2>
    <p>Nome: {{ usuario.nome }}</p>
    <p>Email: {{ usuario.email }}</p>
    <p>Data de Nascimento: {{ usuario.datanasc }}</p>
    <p>Endereço: {{ usuario.endereco }}</p>
    <p>Cidade: {{ usuario.cidade }}</p>
    <p>Estado: {{ usuario.estado }}</p>
    <p>Hobbies: {{ usuario.hobbies }}</p>
    <p>Linguagem de Programação: {{ usuario.linguagemdeprog }}</p>
    <p>Biografia: {{ usuario.biografia }}</p>
    <button @click="editarPerfil" id="editar">Editar perfil</button>
  </div>
  <div v-else>
    <form @submit.prevent="editarPerfil">
      <div id="formulario">
        <p>Insira seu nome:</p>
        <input type="text" v-model="usuario.nome" maxlength="20" minlength="3" required />
        <p>Insira seu email:</p>
        <input type="email" v-model="usuario.email" maxlength="20" minlength="3" required />
        <p>Insira sua senha:</p>
        <input type="password" v-model="usuario.senha" required />
        <p>Confirme sua senha:</p>
        <input type="password" v-model="senha" required />
        <p>Insira sua data de nascimento:</p>
        <input type="date" v-model="usuario.datanasc" required />
        <p>Insira seu endereço:</p>
        <input type="text" v-model="usuario.endereco" required />
        <p>Insira sua cidade:</p>
        <input type="text" v-model="usuario.cidade" required />
        <p>Insira seu estado:</p>
        <select v-model="usuario.estado">
          <option value="">Selecionar Estado</option>
          <option v-for="(value, key) in estados" :key="key" :value="key">{{ value }}</option>
        </select>
        <p>Insira seus hobbies:</p>
        <input type="text" v-model="usuario.hobbies" />
        <p>Insira sua linguagem de programação:</p>
        <input type="text" v-model="usuario.linguagemdeprog" />
        <p>Insira sua biografia:</p>
        <input type="text" v-model="usuario.biografia" />
        <br />
        <button @click="editarPerfil" type="submit" id="editar">Confirmar Edição</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
#editar {
  width: 200px;
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
#formulario{
  color: rgb(0, 0, 0);
  text-align: left;
  width: 450px;
  display: flex;
  flex-direction: column;
}
</style>
