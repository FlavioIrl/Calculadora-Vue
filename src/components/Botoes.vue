<script setup>  
    const props = defineProps([
    'apagarTudo',
    'apagarUltimo',
    'clickOperador',
    'ErroOuInvalido',
    'calcular',
    'clickNumero',
    'clickVirgula',
    'resultado',
  ])
</script>

<template>
    <div class="container">
        <div class="row g-2 botoes">
        <div class="col-6"><i @click="apagarUltimo" class="bi bi-backspace btn btn-letra w-100 "></i></div>
        <div class="col-3"><button class="btn btn-letra w-100 " @click="apagarTudo">C</button></div>
        <div class="col-3"><button class="btn btn-sinais w-100 " @click="clickOperador('/')" :disabled="ErroOuInvalido(resultado)">/</button>
        </div>

        <div class="col-3" v-for="n in ['7', '8', '9']" :key="n">
            <button class="btn w-100 " @click="clickNumero(n)" :disabled="ErroOuInvalido(resultado)">{{ n }}</button>
        </div>

        <div class="col-3">
            <button class="btn btn-sinais w-100 " @click="clickOperador('x')" :disabled="ErroOuInvalido(resultado)">X</button>
        </div>

        <div class="col-3" v-for="n in ['4', '5', '6']" :key="n">
            <button class="btn w-100" @click="clickNumero(n)" :disabled="ErroOuInvalido(resultado)">{{ n }}</button>
        </div>
        <div class="col-3">
            <button class="btn btn-sinais w-100 " @click="clickOperador('-')" :disabled="ErroOuInvalido(resultado)">-</button>
        </div>

        <div class="col-3" v-for="n in ['1', '2', '3']" :key="n">
            <button class="btn w-100 " @click="clickNumero(n)" :disabled="ErroOuInvalido(resultado)">{{ n }}</button>
        </div>
        
        <div class="col-3">
            <button class="btn btn-sinais w-100 " @click="clickOperador('+')" :disabled="ErroOuInvalido(resultado)">+</button>
        </div>

        <div class="col-6 "><button class="btn w-100 btn-zero " @click="clickNumero(0)" :disabled="ErroOuInvalido(resultado)">0</button></div>
        <div class="col-3"><button class="btn btn-sinais w-100 " @click="clickVirgula" :disabled="ErroOuInvalido(resultado)">,</button></div>
        <div class="col-3"><button class="btn btn-sinais w-100 " @click="calcular" :disabled="ErroOuInvalido(resultado)">=</button></div>
        </div>
    </div>
</template>

<style scoped>

.btn:hover {
  background-color: #5a22d3;
  transform: scale(1.1);
}

.btn {
  color: #fff;
  background-color: #1E2E49;
  font-size: 1.2rem;
  transition: all 0.3s ease;
}

.btn-letra {
  color: #d3ae08;
}

.bi-backspace {
  font-size: 1.2rem;
  cursor: pointer;
  color: #d3ae08;
}

.btn-sinais {
  background-color: #d3ae08;
}
</style>