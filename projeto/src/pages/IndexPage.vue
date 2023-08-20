<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-light-blue-14">
      <q-toolbar>
        <q-toolbar-title>
          Rafael Lucas App
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <q-page class="q-pa-xl">
        <div class="column q-gutter-sm">
          <div>
            <q-select v-model="operacao" :options="listaOperacoes" outlined dense />
          </div>
          <div>
            <q-input label="Primeiro Número" v-model="x" outlined dense />
          </div>
          <div>
            <q-input label="Segundo Número" v-model="y" outlined dense />
          </div>
          <q-card class="q-pa-md">
            Resultado: {{ resultado() }}
          </q-card>
        </div>
      </q-page>
   </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
const listaOperacoes = [{ label: 'Soma (+)', value: '+' }, { label: 'Subtração (-)', value: '-' }, { label: 'Multiplicação (*)', value: '*' }, { label: 'Divisão (/)', value: '/' }]
const x = ref(null)
const y = ref(null)
const operacao = ref(listaOperacoes[0])
const resultado = () => {
  if (!x.value || !y.value) return ''
  switch (operacao.value.value) {
    case '+':
      return parseInt(x.value) + parseInt(y.value)
    case '-':
      return parseInt(x.value) - parseInt(y.value)
    case '*':
      return parseInt(x.value) * parseInt(y.value)
    case '/':
      if (y.value === 0) { return 'Erro! Divisão por zero' } else { return parseInt(x.value) / parseInt(y.value) }
  }
}
</script>
