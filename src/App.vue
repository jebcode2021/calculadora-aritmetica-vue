<script setup>
import { reactive } from 'vue';

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

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora de aritmética</h1>
      <p>
        Digite dois números e selecione a operação desejada para adicionar uma calculadora.
        <br> <br>
        Para filtrar as calculadoras, selecione a operação desejada no campo "Filtrar por operação".
        <br> <br>
        Para excluir uma calculadora, clique no botão "Excluir".
        <br> <br>
        Você já adicionou <strong> {{ estado.calculadoras.length }} </strong> calculadora(s).
      </p>
    </header>

    <form @submit.prevent="adicionarCalculadora">
      <div class="row">
        <div class="col-1">
          <input required type="number" class="form-control" placeholder="Digite" :value="estado.numero1" @change="estado.numero1 = $event.target.value">
        </div>
        <div class="col-1">
          <input required type="number" class="form-control" placeholder="Digite" :value="estado.numero2" @change="estado.numero2 = $event.target.value">
        </div>
        <div class="col-2">
          <select class="form-select" @change="selecionarOperacao($event.target.value)">
            <option selected>Selecione operação</option>
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
        <div class="col">
          <button type="submit" class="btn btn-primary">Adicionar calculadora</button>
        </div>
        <div class="col-2">
          <select @change="evento => estado.filtro = evento.target.value" class="form-select">
            <option selected>Filtrar por operação</option>
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
    </form>

    <div class="row mt-5">
      <div class="col-3 d-flex flex-column" v-for="calculadora in filtrarCalculadora()" :key="calculadora.id">
          <div class="card mt-3">
              <div class="card-body">
                <p class="card-text">ID: {{ calculadora.id }}</p>
                <p class="card-text">Calculadora: {{ calculadora.numero1 }} {{ calculadora.operacao }} {{ calculadora.numero2 }}
                </p>
                <p class="card-text">Resultado: {{ calculadora.resultado }}</p>
                <p class="card-text">Operação: {{ calculadora.operacao }}</p>
                <div class="d-grid gap-2">
                  <button class="btn btn-danger" type="button" @click="excluirCalculadora(calculadora.id)">Excluir</button>
                </div>
              </div>
          </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
