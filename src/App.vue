<script setup>
    import { reactive } from 'vue';

    const estado = reactive({
        operador: 'multiplica',
        val1: null,
        val2: null,
        resultado: null,
    })

    const atualizaVal1 = (evento) => {
        estado.val1 = evento.target.value;
        realizaCalculo();
    }
    const atualizaVal2 = (evento) => {
        estado.val2 = evento.target.value;
        realizaCalculo();
    }
    const atualizaOperador = (evento) => {
        estado.operador = evento.target.value;
        realizaCalculo();
        estado.val1 = null;
        estado.val2 = null;
    }

    const realizaCalculo = () => {
        const operador = estado.operador;
        const val1 = parseFloat(estado.val1);
        const val2 = parseFloat(estado.val2);

        switch (operador) {
            case "multiplica":
                return estado.resultado = val1 * val2;
                break;
            case "divide":
                return estado.resultado = val1 / val2;
                break;
            case "soma":
                return estado.resultado = val1 + val2;
                break;
            case "subtrai":
                return estado.resultado = val1 - val2;
                break;
        }
    }
</script>

<template>
    <div class="container bg-secondary rounded-5 p-5 mt-5">
        <header class="pb-4">
            <h1 class="text-center text-light">Calculadora VueJS</h1>
        </header>
        <div class="row d-flex justify-content-center align-items-center pt-4 pb-4">
            <div class="col-md-3 fs-4">
                <input :value="estado.val1" @change="atualizaVal1" required type="number" class="rounded-3 p-1 w-100 text-center" placeholder="Valor1">
            </div>
            <div class="col-1 fs-3 fw-bold p-0">
                <select @change="atualizaOperador" class="rounded-3 w-100 text-center fw-bold operacao">
                    <option value="multiplica">x</option>
                    <option value="divide">÷</option>
                    <option value="soma">+</option>
                    <option value="subtrai">-</option>
                </select>
            </div>
            <div class="col-md-3 fs-4">
                <input :value="estado.val2" @change="atualizaVal2" required type="number" class="text-center rounded-3 p-1 w-100" placeholder="Valor2">
            </div>

            <div class="col-md-1 text-light igual">
                =
            </div>
            <div class="col-md-2">
                <span class="w-100 fw-bold bg-light ps-5 pe-5 pt-2 pb-2 fs-3 text-primary rounded-1">{{ estado.resultado }}</span>
            </div>
        </div>
        

    </div>
</template>

<style scoped>
    .operacao {
        min-width: 50px;
    }
    .igual {
        font-size: 2em;
    }
</style>