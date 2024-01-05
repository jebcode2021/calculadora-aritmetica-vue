<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeCalculadora.vue';

const estado = reactive({
  calculadoras: [],
  numero1: '',
  numero2: '',
});

const adicionarCalculadora = () => {
  const calculadora = {
    id: estado.calculadoras.length + 1,
    numero1: estado.numero1,
    numero2: estado.numero2,
    operacao: estado.operacao,
    resultado: estado.resultado = eval(`${estado.numero1} ${estado.operacao} ${estado.numero2}`),
  };

  estado.calculadoras.push(calculadora);
  estado.numero1 = '';
  estado.numero2 = '';

  return estado.calculadoras;
};

const selecionarOperacao = (operacao) => {
  estado.operacao = operacao;
  'soma' === operacao ? estado.operacao = '+' : '';
  'subtracao' === operacao ? estado.operacao = '-' : '';
  'multiplicacao' === operacao ? estado.operacao = '*' : '';
  'divisao' === operacao ? estado.operacao = '/' : '';

  estado.operacao.push(operacao);
  estado.operacao = '';
  return estado.operacao;
};

const excluirCalculadora = (id) => {
  estado.calculadoras = estado.calculadoras.filter((calculadora) => calculadora.id !== id);
  return estado.calculadoras;
};

const filtrarCalculadora = () => {
  const { filtro } = estado;
 
  switch (filtro) {
    case 'soma':
      return estado.calculadoras.filter((calculadora) => calculadora.operacao === '+');
    case 'subtracao':
      return estado.calculadoras.filter((calculadora) => calculadora.operacao === '-');
    case 'multiplicacao':
      return estado.calculadoras.filter((calculadora) => calculadora.operacao === '*');
    case 'divisao':
      return estado.calculadoras.filter((calculadora) => calculadora.operacao === '/');
    default:
      return estado.calculadoras;
  }
};

const getNumeroCalculadoras = () => {
  return estado.calculadoras.length;
};

</script>

<template>
  <div class="container">
    <Cabecalho :calculadoras="getNumeroCalculadoras()" />
    <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :numero1="estado.numero1" :numero2="estado.numero2" :editar-calculadora="evento => estado.numero1 = evento.target.value" :editar-calculadora2="evento => estado.numero2 = evento.target.value"  :adicionar-calculadora="adicionarCalculadora" :selecionar-operacao="evento => selecionarOperacao(evento.target.value)" />
    <ListaDeTarefas :calculadoras="filtrarCalculadora()" :excluirCalculadora="excluirCalculadora" />
  </div>
</template>

<style scoped></style>
