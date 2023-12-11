<script setup>
    import {ref} from 'vue'
   /*  import Alerta from './Alerta.vue' */

    const presupuesto = ref(0)
    const error = ref ('')

    const emit = defineEmits(['definir-presupuesto'])

    const definirPresupuesto = () => {
        if (presupuesto.value <= 0 || presupuesto.value === ''){
            error.value = 'Presupuesto no válido'

            setTimeout(()=> {
                error.value = ''
            }, 2000)
            return
        }

        emit('definir-presupuesto', presupuesto.value )
    }
</script>

<template>
    <form
        class="presupuesto"
        @submit.prevent="definirPresupuesto"
    >

        <Alerta 
            v-if="error"
        >
            {{ error }}
        </Alerta>

        <div class="campo">
            <label for="nuevo-presupuesto"> Definir presupuesto</label>
            <input
                id="nuevo-presupuesto"
                class="nuevo-presupuesto"
                placeholder="Añade tu presupuesto"
                type="number"
                min="0"
                v-model.number="presupuesto"
            />
        
        <input type="submit" value="Definir Presupuesto"/>
    </div>
    </form>
</template>

<style scoped>
    .presupuesto{
        width: 100%;
    }
    .campo{
        display: grid;
        /* align-content: center; */
        gap: 2rem
    }
    .presupuesto label {
        font-size: 2.2rem;
        text-align: center;
        color: var(--azul);
    }
    .presupuesto input[type="number"] {
        background-color: var(--gris-claro);
        border-radius: 1rem;
        padding: 1rem;
        border: none;
        font-size: 2.2rem;
        text-align: center;
    }
    .presupuesto input[type="submit"] {
        /* outline:black 2px solid; */
        background-color: var(--azul);
        /* width: 60%; */
        border-radius: 1rem;
        padding: 1rem;
        margin-top: 2rem;        
        border: none;
        font-size: 2rem;
        font-weight: 900;
        text-align: center;
        color: var(--blanco);
        transition: background-color 300ms ease;
    }
    .presupuesto input[type="submit"]:hover {
        background-color: #1048a4;
        cursor: pointer;
    }

</style>