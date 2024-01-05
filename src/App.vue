<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue'
import Operacao from './components/Operacao.vue'
import Resultado from './components/Resultado.vue'
import Footer from './components/footer.vue';

const estado = reactive({
  operation: '+',
  numero1: '',
  numero2: ''
})

const resultado = () => {
  const { operation } = estado
  switch (operation) {
    case '-':
      return parseFloat(estado.numero1) - parseFloat(estado.numero2)
    case '*':
      return parseFloat(estado.numero1) * parseFloat(estado.numero2)
    case '/':
      return parseFloat(estado.numero1) / parseFloat(estado.numero2)
    default:
      return parseFloat(estado.numero1) + parseFloat(estado.numero2)
  }
}


</script>

<template>
  <div class="container">
    <Cabecalho />
    <Operacao :operacao="evento => estado.operation = evento.target.value" :numero1="evento => estado.numero1 = evento.target.value" :numero2="evento => estado.numero2 = evento.target.value" />
    <Resultado :numero1="estado.numero1" :numero2="estado.numero2" :resultado="resultado()" />
    <Footer />
  </div>
</template>

<style scope>
.container {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-top: 20px;
  margin-bottom: 20px;
  box-shadow: 0 0 10px #ccc;
}
</style>