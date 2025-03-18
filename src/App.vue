<script setup>
import { computed, reactive } from 'vue'

const estado = reactive ({
  primeiroNumero: '',
  segundoNumero: '',
  operador: '',
  resultado: '',
 })

 function apagarOp() {
  if (estado.segundoNumero !== '') {
    estado.segundoNumero = estado.segundoNumero.slice(0, -1)
  } else if (estado.operador !== '') {
    estado.operador = ''
  } else if (estado.primeiroNumero !== '') {
    estado.primeiroNumero = estado.primeiroNumero.slice(0, -1)
  }
  // estado.primeiroNumero = ''
  // estado.operador = ''
 }
 const visor = computed(()=> {
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
      return number2 !== 0 ? number1 / number2:
      'Erro'
    default:
      return ''
    }
 })
 
 function clickVirgula() {
  if(estado.operador === '') {
      if (! estado.primeiroNumero.includes(',')) {
        estado.primeiroNumero += ','
      }
    }else {
    if(! estado.segundoNumero.includes(',')) {
      estado.segundoNumero += ','
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

 function limparC() {
  estado.primeiroNumero = ''
  estado.segundoNumero = ''
  estado.operador = ''
  estado.resultado = ''

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
  <div class="container">
    <div class="calculadora mt-5 p-3 rounded-5">
      <header>
        <h1 class="title text-start">Calculadora</h1>
        <div class="row text-end visor-operacao visor">
          <h1 >{{  visor }}</h1>
          <h2 class="visor-resultado text-end" >{{ resultado }}</h2>
        </div>
      </header>
      <div class="container">
        <div class="row g-2 botoes">
          <div class="col-3"><button class="btn btn-letra w-100 rounded-pill" @click="apagarOp">CE</button></div>
          <div class="col-3"><button class="btn btn-letra w-100 rounded-pill" @click="limparC">C</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">%</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill" @click= "clickOperador('/')">/</button></div>
          
          <div class="col-3" v-for="n in ['7', '8', '9']" key="n"><button class="btn w-100 rounded-pill" @click="clickNumero(n)">{{ n }}</button></div>

          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill" @click= "clickOperador('x')">X</button></div>
          
          <div class="col-3" v-for="n in ['4', '5', '6']" key="n"><button class="btn w-100 rounded-pill" @click="clickNumero(n)">{{ n }}</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill" @click= "clickOperador('-')" >-</button></div>
          
          <div class="col-3" v-for="n in ['1', '2', '3']" key="n"><button class="btn w-100 rounded-pill" @click="clickNumero(n)">{{ n }}</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill" @click= "clickOperador('+')">+</button></div>
          
          <div class="col-6 "><button class="btn w-100 btn-zero rounded-pill" @click="clickNumero(0)">0</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill" @click="clickVirgula">,</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill" @click="calcular">=</button></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.btn:hover {
  background-color: #5a22d3; /* Mudando a cor de fundo */
  transform: scale(1.1); /* Aumentando o tamanho do botão */
}

.btn {
  color: #fff;
  background-color: #1E2E49;
  font-size: 2rem;
  transition: all 0.3s ease; /* Transição suave */
}
.btn-letra {
  color: #d3ae08;
}
.btn-sinais{
  background-color: #d3ae08;
}

.calculadora {
  background-image: linear-gradient(to bottom , #28166b 20%, #0c0720);
  font-family: "Rubik", sans-serif;
  border: 10px solid rgb(16, 8, 22);
  max-width: 360px;
  margin: 0 auto;
  padding: 20px;
}

.visor-operacao {
  border: none;
  background-color: transparent;
  color: #fff;
  font-size: 2rem;
  min-height: 250px;

  display: flex;
  align-items: center;
  justify-content: flex-end;
  overflow-x: auto;
}

.visor-resultado {
  color: #737eac;
  font-size: 1.6rem;
  margin-bottom: 150px;
}

.title {
  color: #737eac;
  font-size: 1.5rem;
  margin-bottom: 40px;
}
</style>
