<script setup>
import { reactive } from 'vue';

// import  Algarismos from './components/Algarismos.vue';
// import Resultado from './components/Resultado.vue';

import { ref } from 'vue';

const numero1 = ref('');
const operacao = ref('');
const numero2 = ref('');

const calcularResultado = () => {
  if (numero1.value !== '' && numero2.value !== '') {
    switch (operacao.value) {
      case 'soma':
        resultado.value = Number(numero1.value) + Number(numero2.value);
        break;
      case 'subtracao':
        resultado.value = Number(numero1.value) - Number(numero2.value);
        break;
      case 'multiplicacao':
        resultado.value = Number(numero1.value) * Number(numero2.value);
        break;
      case 'divisao':
        resultado.value = Number(numero1.value) / Number(numero2.value);
        break;
      default:
        resultado.value = '';
    }
  }
};

const resultado = ref('');

</script>

<template>
  <div class="container d-flex flex-column vh-100 justify-content-center col-12">
    <h1 class="col-12 d-flex justify-content-center pb-3">Calculadora Aritmética</h1>

    <!-- Formulário -->
    <form @submit.prevent="calcularResultado">
      <div class="row">
        <div class="col">
          <input v-model="numero1" @input="calcularResultado" type="text" placeholder="Digite aqui o primeiro número" class="form-control text-center">
        </div>
        <div class="col-md-1">
          <select @change="calcularResultado" v-model="operacao" class="form-control text-center">
            <option value="soma"> + </option>
            <option value="subtracao"> - </option>
            <option value="multiplicacao"> x </option>
            <option value="divisao"> / </option>
          </select>
        </div>
        <div class="col">
          <input v-model="numero2" @input="calcularResultado" type="text" placeholder="Digite aqui o segundo número" class="form-control text-center">
        </div>
      </div>
    </form>

    <!-- Resultado -->
    <div v-if="numero1 !== '' && numero2 !== '' && operacao !== ''" class="p-5 mb-4 mt-4 bg-light rounded-3 d-flex justify-content-center">
      <h2>
        O resultado é: {{ resultado }}
      </h2>
    </div>
    <div v-else class="p-5 mb-4 mt-4 bg-light rounded-3 d-flex justify-content-center">
      <h2>
        Digite os números e selecione a operação.
      </h2>
    </div>
  </div>
</template>


<style scoped></style>
