<script setup>
const props = defineProps(['adicionarCalculadora', 'numero1', 'numero2', 'trocarFiltro', 'editarCalculadora', 'editarCalculadora2', 'selecionarOperacao']);
</script>

<template>
  <form @submit.prevent="props.adicionarCalculadora">
    <div class="row">
      <div class="col-1">
        <input required type="number" class="form-control" placeholder="Digite" :value="props.numero1"
          @change="props.editarCalculadora">
      </div>
      <div class="col-1">
        <input required type="number" class="form-control" placeholder="Digite" :value="props.numero2"
          @change="props.editarCalculadora2">
      </div>
      <div class="col-2">
        <select class="form-select" @change="props.selecionarOperacao">
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
        <select @change="props.trocarFiltro" class="form-select">
          <option selected>Filtrar por operação</option>
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
    </div>
  </form>
</template>