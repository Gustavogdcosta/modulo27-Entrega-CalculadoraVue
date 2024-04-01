<script setup>
import { reactive } from 'vue';

const calculadora = reactive({
  operacao: 'Adição',
  campos: [
    {
      campoA: 0,
      campoB: 0,
    }
  ]
})

const Resultado = () => {
  if (calculadora.operacao == 'Adição') {
    const soma = parseInt(calculadora.campoA) + parseInt(calculadora.campoB);
    return (soma)
  }
  if (calculadora.operacao == 'Subtração') {
    const diminuir = parseInt(calculadora.campoA) - parseInt(calculadora.campoB);
    return (diminuir)
  }
  if (calculadora.operacao == 'Multiplicação') {
    const multiplica = parseInt(calculadora.campoA) * parseInt(calculadora.campoB);
    return (multiplica)
  }
  if (calculadora.operacao == 'Divisão') {
    const divide = parseInt(calculadora.campoA) / parseInt(calculadora.campoB);
    return (divide)
  }
}
</script>

<template>
  <form>
    <div class="row formulario">
      <div class="col-4">
        <input type="number" placeholder="Digite o valor 1" class="form-control" required :value="calculadora.campoA"
          @keyup="evento => calculadora.campoA = evento.target.value">
      </div>
      <div class="col-4">
        <input type="number" placeholder="Digite o valor 2" class="form-control" required :value="calculadora.campoB"
          @keyup="evento => calculadora.campoB = evento.target.value">
      </div>
      <div class="col-4">
        <select @change="evento => calculadora.operacao = evento.target.value">
          <option value="Adição">Adição</option>
          <option value="Subtração">Subtração</option>
          <option value="Multiplicação">Multiplicação</option>
          <option value="Divisão">Divisão</option>
        </select>
      </div>
    </div>
    <div class="row ">
      <div class="col formulario">
        <h2> O Resultado da operação é: {{ Resultado() }}</h2>
      </div>
    </div>
  </form>
</template>

<style scoped>
.formulario {
  margin: 100px 20% 0 20%;
  align-items: center;
  text-align: center;
}
</style>
