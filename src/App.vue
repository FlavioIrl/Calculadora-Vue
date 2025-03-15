<script setup>

</script>

<template>
  <div class="container">
    <div class="calculadora mt-5 p-4 rounded-5">
      <header>
        <h1 class="title text-start">Calculadora</h1>
        <div class="visor text-end">
          <h1 class="visor-operacao">110+100</h1>
          <h2 class="visor-resultado" >200</h2>
        </div>
      </header>
      <div class="container">
        <div class="row g-2 botoes">
          <div class="col-3"><button class="btn w-100 rounded-pill">7</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">8</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">9</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">+</button></div>
          
          <div class="col-3"><button class="btn w-100 rounded-pill">4</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">5</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">6</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">-</button></div>
          
          <div class="col-3"><button class="btn w-100 rounded-pill">1</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">2</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">3</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">x</button></div>
          
          <div class="col-3"><button class="btn w-100 rounded-pill">0</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">.</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">=</button></div>
          <div class="col-3"><button class="btn w-100 rounded-pill">/</button></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.btn {
  color: #fff;
  background-color: #1E2E49;
  font-size: 1.2rem;
}
.calculadora {
  background-color: #333A58;
  font-family: "Rubik", sans-serif;
  border: 10px solid #202642;
  max-width: 360px;
  margin: 0 auto;
  padding: 20px;
}

.visor-operacao {
  color: #fff;
  font-size: 2rem;
}

.visor-resultado {
  color: #737eac;
  font-size: 1rem;
  margin-bottom: 150px;
}

.title {
  color: #737eac;
  font-size: 1.5rem;
  margin-bottom: 40px;
}
</style>
