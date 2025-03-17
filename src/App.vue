<script setup>

</script>

<template>
  <div class="container">
    <div class="calculadora mt-5 p-3 rounded-5">
      <header>
        <h1 class="title text-start">Calculadora</h1>
        <div class="row justify-content-end visor">
          <div class="col-2"><h1 class="visor-operacao">110</h1></div>
          <div class="col-1"><h1 class="visor-operacao">+</h1></div>
          <div class="col-3"><h1 class="visor-operacao">100</h1></div>
        </div>
        <h2 class="visor-resultado text-end" >210</h2>
      </header>
      <div class="container">
        <div class="row g-2 botoes">
          <div class="col-3"><button class="btn btn-letra w-100 rounded-pill">CE</button></div>
          <div class="col-3"><button class="btn btn-letra w-100 rounded-pill">C</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">%</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill">/</button></div>
          
          <div class="col-3"><button class="btn w-100 rounded-pill">7</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">8</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">9</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill">X</button></div>
          
          <div class="col-3"><button class="btn w-100 rounded-pill">4</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">5</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">6</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill">-</button></div>
          
          <div class="col-3"><button class="btn w-100 rounded-pill">1</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">2</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">3</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill">+</button></div>
          
          <div class="col-6 "><button class="btn w-100 btn-zero rounded-pill">0</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill">,</button></div>
          <div class="col-3"><button class="btn btn-sinais w-100 rounded-pill">=</button></div>
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
  background-image: linear-gradient(to bottom , #3a2d68 30%, #2f155e);
  font-family: "Rubik", sans-serif;
  border: 10px solid rgb(51, 32, 66);
  max-width: 360px;
  margin: 0 auto;
  padding: 20px;
}

.visor-operacao {
  border: none;
  background-color: transparent;
  color: #fff;
  font-size: 2rem;
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
