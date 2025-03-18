<script setup>
    const props = defineProps([ 'resultado', 'visor'])
</script>

<template>
    <header>
          <h1 class="title text-start">Calculadora</h1>
          <div class="row text-end visor-operacao visor">
            <h1>{{ props.visor }}</h1>
            <h2 class="visor-resultado text-end">{{ props.resultado }}</h2>
          </div>
    </header>
</template>

<style scoped>

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