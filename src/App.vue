<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue'
import Formulario from './components/Formulario.vue';

const pacientes = ref([])
</script>

<template>
  <div class="container mx-auto mt-20">
      <Header />
      <div class="mt-12 md:flex">
         <Formulario />
         <div class="md:w-1/2 md:h-screen overflow-y-scroll">
            <h3 class="font-black text-3xl text-center">
              Administra tus paciente
            </h3>

            <div v-if="pacientes.length > 0">

            </div>
            <p v-else class="mt-10 text-2xl text-center">
              Actualmente no hay pacientes
            </p> 
         </div>
      </div>

  </div>
</template>

<style scoped>
</style>
