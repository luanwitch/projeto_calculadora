<script setup>
import { ref, computed } from "vue";

// Definindo as variáveis reativas
const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref("+");

// Usando computed para calcular o resultado dinamicamente
const calcular = computed(() => {
  switch (operacao.value) {
    case "+":
      return numero1.value + numero2.value;
    case "-":
      return numero1.value - numero2.value;
    case "*":
      return numero1.value * numero2.value;
    case "/":
      return numero2.value !== 0
        ? numero1.value / numero2.value
        : "Erro: Divisão por 0";
    default:
      return 0;
  }
});
</script>

<template>
  <div class="calculadora">
    <h1>Calculadora Aritmética</h1>

    <div>
      <label for="numero1">Número 1:</label>
      <input
        id="numero1"
        v-model.number="numero1"
        type="number"
        placeholder="Digite o número 1"
      />
    </div>

    <div>
      <label for="numero2">Número 2:</label>
      <input
        id="numero2"
        v-model.number="numero2"
        type="number"
        placeholder="Digite o número 2"
      />
    </div>

    <div>
      <label for="operacao">Operação:</label>
      <select id="operacao" v-model="operacao">
        <option value="+">Soma</option>
        <option value="-">Subtração</option>
        <option value="*">Multiplicação</option>
        <option value="/">Divisão</option>
      </select>
    </div>

    <div>
      <h2>Resultado: {{ calcular }}</h2>
    </div>
  </div>
</template>

<style scoped>
.calculadora {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

div {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input,
select {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  box-sizing: border-box;
}
</style>
