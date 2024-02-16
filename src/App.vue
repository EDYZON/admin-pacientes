<script setup>
import { ref , reactive } from 'vue';
import { uid } from 'uid';
import Header from './components/Header.vue'
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

const pacientes = ref([])
const paciente = reactive({
    uid:null,
    nombre:'',
    propietario:'',
    email:'',
    alta:'',
    sintomas:''
})
const guardarPaciente = () =>{
  pacientes.value.push({
    ...paciente,
    id: uid()
  })

  //reiniciar el objeto
  /*
  paciente.nombre = ''
  paciente.propietario = ''
  paciente.email = ''
  paciente.alta = ''
  paciente.sintomas = ''
  paciente.nombre = ''*/

  //otra formas
  Object.assign(paciente,{
  nombre : '',
  propietario : '',
  email : '',
  alta : '',
  sintomas : '',
  nombre : '',
  })

 const actualizarPaciente = (id)=>{
  console.log('actualizando',id);
 }

}
</script>

<template>
  <div class="container mx-auto mt-20">
      <Header />
      <div class="mt-12 md:flex">
         <Formulario 
         v-model:nombre="paciente.nombre"
         v-model:email="paciente.email"
         v-model:paciente="paciente.alta"
         v-model:sintomas="paciente.sintomas"
         @guardar-paciente="guardarPaciente"
         />
         <div class="md:w-1/2 md:h-screen overflow-y-scroll">
            <h3 class="font-black text-3xl text-center">
              Administra tus paciente
            </h3>

            <div v-if="pacientes.length > 0">
              <p class="text-lg mt-5 text-cennter mb-10">
                 información de <span class="text-indigo-600 font-bold">Pacientes</span>
              </p>
                <Paciente
                 v-for="paciente in pacientes"
                 :paciente="paciente"
                 @actualizar-paciente="actualizarPaciente"
                />
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
