<script setup>
 import { computed } from 'vue';

 const prop = defineProps({
    alerta:{
        type:Object,
        required:true
    }
 })

 const isError = computed(()=>{
   return 'Esta es la función'
 });
</script>

<template>
    <div
    :class="[isError ? 'bg-red-500' : 'bg-green-500']"
    class="text-white text-center p3 uppercase font-bold mb-3 rounded-md"
    >
        {{ alerta.mensaje }}
    </div>
</template>


