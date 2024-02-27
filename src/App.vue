<script setup>
import { reactive } from 'vue';

const nome = "Douglas Medina"
const meuObj = {
  nome: "Douglas",
  filmeFavorit: "Batman"
}

function dizOla(nome) {
  return `${nome} diz oi`;
}

const enderecoImagemBatman = "https://assets.nintendo.com/image/upload/ar_16:9,c_lpad,w_1240/b_white/f_auto/q_auto/ncom/software/switch/70070000018073/30648e0a24cff549fe97f586431b4b927a8e49f3531108ec50fd00a106733b4d"
const imagemSuperman = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQtYACxguDLzxgzPp-8gWM7CRDVSFviageX8WjNSeIc&s"

const botaoEstaDesabilitado = false

const gostaDoBatman = false
const gostaDoSuperman = false

const estaAutorizado = false

// let contador = 0

const estado = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferindo: 0,
})

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function alteraEmail(evento) {
  estado.email = evento.target.value;
}

function mostraSaldoFuturo() {
  const { saldo, transferindo} = estado;
  return saldo - transferindo
}

function validaValorTransferencia() {
  const { saldo, transferindo} = estado;
  return saldo >= transferindo
}

</script>


<template>
  <h1>{{ dizOla("Ana") }}</h1>
  <img v-if="gostaDoBatman" :src="enderecoImagemBatman" alt="">
  <img v-else-if="gostaDoSuperman" :src="imagemSuperman" alt="">
  <h2 v-else>Não curte heróis da DC</h2>

  <h1 v-if="estaAutorizado">Bem vindo</h1>
  <h1 v-else>Não possui acesso</h1>
  
  <button :disabled="botaoEstaDesabilitado">enviar mensagem</button>

  <br />
  <hr />

  {{ estado.contador }}

  <button @click="incrementar" type="button">+</button>
  <button @click="decrementar" type="button">-</button>

  <br />
  <hr />

  {{ estado.email }}
  <!-- <input type="email" @change="alteraEmail"> -->
  <input type="email" @keyup="alteraEmail">

  <br />
  <hr />


  Saldo: {{ estado.saldo }} <br />
  Transferido: {{ estado.transferindo }} <br />
  Saldo depois da transferência: {{ mostraSaldoFuturo() }} <br />
  <input class="campo" :class="{ invalido: !validaValorTransferencia() }" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir">
  <button v-if="validaValorTransferencia()">Transferir</button>
  <span v-else>Saldo insuficiente.</span>

</template>

<style scoped>
  img {
    max-width: 200px;
  }

  .invalido {
    outline-color: red;
    border-color: red;
  }

  .campo {
    border: 2px solid #000;
  }
</style>
