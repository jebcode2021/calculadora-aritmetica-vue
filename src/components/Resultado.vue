<script setup>
const props = defineProps(['numero1', 'numero2', 'resultado'])
</script>

<template>
    <div class="col-md-12">
        <div class="form-floating mb-3 mt-3">
            <div class="input-group">
                <smal class="input-group-text">=</smal>
                <input type="number" class="form-control" placeholder="Resultado" disabled  v-if="props.numero1 && props.numero2 != ''" :value="props.resultado"/>
                <input type="number" class="form-control" placeholder="Resultado" disabled  v-else-if="props.numero1 || props.numero2 === ''"/>
            </div>
        </div>
    </div>
</template>
