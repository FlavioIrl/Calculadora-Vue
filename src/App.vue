<script setup>
import { computed, reactive } from 'vue'
import Visor from './components/Visor.vue'
import Botoes from './components/Botoes.vue'
import 'bootstrap-icons/font/bootstrap-icons.css';

const estado = reactive({
  primeiroNumero: '',
  segundoNumero: '',
  operador: '',
})

function apagarUltimo() {
  if (estado.segundoNumero !== '') {
    estado.segundoNumero = estado.segundoNumero.slice(0, -1)
  } else if (estado.operador !== '') {
    estado.operador = ''
  } else if (estado.primeiroNumero !== '') {
    estado.primeiroNumero = estado.primeiroNumero.slice(0, -1)
  }
}
const visor = computed(() => {
  return `${estado.primeiroNumero}${estado.operador}${estado.segundoNumero}`
})

const resultado = computed(() => {
  const number1 = parseFloat(estado.primeiroNumero);
  const number2 = parseFloat(estado.segundoNumero);

  if (isNaN(number1) || isNaN(number2) || estado.operador === '') return ''

  switch (estado.operador) {
    case '+':
      return number1 + number2
    case '-':
      return number1 - number2
    case 'x':
      return number1 * number2
    case '/':
      return number2 !== 0 ? number1 / number2 : "ERRO 404!"
    default:
      return ''
  }
})

function ErroOuInvalido(resultado) {
  return resultado === 'Erro' || resultado === null || isNaN(resultado) || !isFinite(resultado);
}
function clickVirgula() {
  if (estado.operador === '') {
    if (!estado.primeiroNumero.includes('.')) {
      estado.primeiroNumero += '.'
    }
  } else {
    if (!estado.segundoNumero.includes('.')) {
      estado.segundoNumero += '.'
    }
  }
}
function clickNumero(number) {
  if (estado.operador === '') {
    estado.primeiroNumero += number
  } else {
    estado.segundoNumero += number
  }
}

function clickOperador(op) {
  if (estado.primeiroNumero !== '') {
    estado.operador = op
  }
}

function apagarTudo() {
  estado.primeiroNumero = ''
  estado.segundoNumero = ''
  estado.operador = ''
}

function calcular() {
  if (resultado.value !== '') {
    estado.primeiroNumero = resultado.value.toString()
    estado.segundoNumero = ''
    estado.operador = ''
  }
}
</script>

<template>
  <div class="fundo">
    <div class="container">
      <div class="calculadora mt-1 p-3 rounded-5">
        <Visor :resultado="resultado" :visor="visor"/>
        <Botoes :-erro-ou-invalido="ErroOuInvalido" :calcular="calcular" 
        :apagar-tudo="apagarTudo" 
        :apagar-ultimo="apagarUltimo"
        :click-numero="clickNumero"
        :click-virgula="clickVirgula"
        :click-operador="clickOperador"
        :resultado="resultado"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.fundo {
  background: radial-gradient(circle at center, #27416d, #0c0720 90%);
  position: absolute;
  width: 100%;
  height: 100%;
}

.calculadora {
  background-image: linear-gradient(to bottom, #28166b 20%, #0c0720);
  font-family: "Rubik", sans-serif;
  border: 10px solid rgb(16, 8, 22);
  max-width: 280px;
  margin: 0 auto;
  padding: 20px;
}
</style>