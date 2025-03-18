<script setup>
import { computed, reactive } from 'vue'
import Visor from './components/Visor.vue'
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

.calculadora {
  background-image: linear-gradient(to bottom, #28166b 20%, #0c0720);
  font-family: "Rubik", sans-serif;
  border: 10px solid rgb(16, 8, 22);
  max-width: 280px;
  margin: 0 auto;
  padding: 20px;
}

.visor-operacao {
  border: none;
  background-color: transparent;
  border: none;
  background-color: transparent;
  color: #fff;
  font-size: 2rem;
  min-height: 250px;

  display: flex;
  align-items: center;
  justify-content: flex-end;
  overflow-x: auto;
  min-height: 250px;

  display: flex;
  align-items: center;
  justify-content: flex-end;
  overflow-x: auto;
}

.visor-resultado {
  color: #737eac;
  font-size: 1.6rem;
  font-size: 1.6rem;
  margin-bottom: 150px;
}

.title {
  color: #737eac;
  font-size: 1.5rem;
  margin-bottom: 40px;
}
</style>