<script setup>
const props = defineProps(['operacao', 'numero1', 'numero2'])
</script>

<template>
    <p class="lead text-center">
        Você pode fazer operações matemáticas simples, como soma, subtração, multiplicação e divisão.
    </p>
    <div class="formOperacao">
        <select @change="props.operacao" class="form-select">
            <option value="+">Soma +</option>
            <option value="-">Subtração -</option>
            <option value="*">Multiplicação *</option>
            <option value="/">Divisão /</option>
        </select>
    </div>

    <div class="row">
        <div class="col-md-6">
            <div class="form-floating mb-3 mt-3">
                <input @keyup="props.numero1" required type="number" class="form-control" placeholder="Insira o número 1" />
                <label for="numero1">Número 1</label>
            </div>
        </div>

        <div class="col-md-6">
            <div class="form-floating mb-3 mt-3">
                <input @keyup="props.numero2" required type="number" class="form-control" placeholder="Insira o número 2" />
                <label for="numero2">Número 2</label>
            </div>
        </div>
    </div>
</template>

<style scope>
select {
    width: 30%;
    margin: 0 auto;
    text-align: center;
}

.formOperacao {
    width: 20%;
    margin: 0 auto;
}
</style>