<script setup>
const pros = defineProps(['calculadoras', 'filtro', 'excluirCalculadora']);
</script>

<template>
    <div class="row mt-5">
        <div class="col-3 d-flex flex-column" v-for="calculadora in pros.calculadoras" :key="calculadora.id">
            <div class="card mt-3">
                <div class="card-body">
                    <p class="card-text">ID: {{ calculadora.id }}</p>
                    <p class="card-text">Calculadora: {{ calculadora.numero1 }} {{ calculadora.operacao }} {{
                        calculadora.numero2 }}
                    </p>
                    <p class="card-text">Resultado: {{ calculadora.resultado }}</p>
                    <p class="card-text">Operação: {{ calculadora.operacao }}</p>
                    <div class="d-grid gap-2">
                        <button class="btn btn-danger" type="button" @click="pros.excluirCalculadora(calculadora.id)">
                            Excluir
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>