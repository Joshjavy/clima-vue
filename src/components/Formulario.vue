<script setup>
    import Alerta from './Alerta.vue'
    import { reactive, ref} from 'vue'
        const busqueda = reactive({
            ciudad :'',
            pais:'',
        })

    const error =ref ('');
    
    const emit = defineEmits(['obtener-climna']);



    const paises = [
        { codigo: 'US', nombre: 'Estados Unidos' },
        { codigo: 'MX', nombre: 'México' },
        { codigo: 'AR', nombre: 'Argentina' },
        { codigo: 'CO', nombre: 'Colombia' },
        { codigo: 'CR', nombre: 'Costa Rica' },
        { codigo: 'ES', nombre: 'España' },
        { codigo: 'PE', nombre: 'Perú' }
    ];

    const consultarClima =()=>{
        if(Object.values(busqueda).includes('')){
            error.value ='Todos los campos son obligatorios';
            return;
        }
        error.value ='';  
        emit('obtener-climna',busqueda);

    }

</script>
<template>
    <form class="formulario"
        @submit.prevent="consultarClima"
    >
        <Alerta v-if="error">
            {{ error }}
        </Alerta>
        <div class="campo">
            <label for="ciudad">Ciudad</label>
            <input type="text"
                id="ciudad"
                placeholder="Ciudad"
                class=""
                v-model="busqueda.ciudad"
            />
        </div>

        <div class="campo">
            <label for="pais">pais</label>
            <select id="pais"
                v-model="busqueda.pais"
            >
                <option value=""> -- Seleccione un pais -- </option>
                <option 
                v-for="pais in paises"
                :value="pais.codigo"
                >
                    {{ pais.nombre }}
                </option>
            </select>
        </div>
        <input type="submit" value="Consultar Clima">
    </form>
</template>