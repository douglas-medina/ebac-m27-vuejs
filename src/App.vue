<script setup>
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
</script>


<template>
  <h1>{{ dizOla("Ana") }}</h1>
  <img v-if="gostaDoBatman" :src="enderecoImagemBatman" alt="">
  <img v-else-if="gostaDoSuperman" :src="imagemSuperman" alt="">
  <h2 v-else>Não curte heróis da DC</h2>

  <h1 v-if="estaAutorizado">Bem vindo</h1>
  <h1 v-else>Não possui acesso</h1>
  
  <button :disabled="botaoEstaDesabilitado">enviar mensagem</button>
</template>

<style scoped>
  img {
    max-width: 200px;
  }
</style>
