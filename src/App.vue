<script setup>
    import useClima from './composables/useClima';
    import Formulario from './components/Formulario.vue'
    const { obtenerClima } = useClima();
</script>

<template>
    <h1 class="titulo">Buscador de clima</h1>
    <div class="contenedor buscador-clima">
        <Formulario 
            @obtener-climna="obtenerClima"
        />
    </div>
    
</template>