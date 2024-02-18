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

const botaoEstaDesabilitado = true

</script>


<template>
  <h1>{{ dizOla("Ana") }}</h1>
  <img :src="enderecoImagemBatman" alt="">

  <button :disabled="botaoEstaDesabilitado">enviar mensagem</button>
</template>

<style scoped>

</style>
