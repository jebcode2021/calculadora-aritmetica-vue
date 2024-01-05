<script setup>
const props = defineProps(['calculadoras']);
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Calculadora de aritmética</h1>
    <p>
      Digite dois números e selecione a operação desejada para adicionar uma calculadora.
      <br> <br>
      Para filtrar as calculadoras, selecione a operação desejada no campo "Filtrar por operação".
      <br> <br>
      Para excluir uma calculadora, clique no botão "Excluir".
      <br> <br>
      Você já adicionou <strong> {{ props.calculadoras }} </strong> calculadora(s).
    </p>
  </header>
</template>