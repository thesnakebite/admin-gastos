<script setup>
    import { ref } from 'vue'
    import Alerta from './Alerta.vue'

    const presupuesto = ref(0)
    const error = ref('')

    const definirPresupuesto = () => {
        if (presupuesto.value <= 0) {
            error.value = 'Presupuesto no válido'

            setTimeout( () => {
                error.value= ''
            }, 2000)
        }
    }
</script>

<template>
    <form class="presupuesto" 
          @submit.prevent="definirPresupuesto" 
    >

    <transition name="alerta">
        <Alerta v-if="error">
            {{ error }}
        </Alerta>
    </transition>
    
        <div class="campo">
            <label for="nuevo-presupuesto">Definir Presupuesto</label>

            <input id="nuevo-presupuesto"
                   class="nuevo-presupuesto"
                   placeholder="Añade tu presupuesto" 
                   type="number"
                   min="0"
                   v-model.number="presupuesto"
            />
        </div>

        <input type="submit" value="Definir Presupuesto" />
    </form>
</template>

<style scoped>
    .presupuesto {
        width: 100%;

    }

    .campo {
        display: grid;
        gap: 2rem;
    }

    .presupuesto label {
        font-size: 2.2rem;
        font-weight: 800;
        text-align: center;
        color: var(--blue);
    }

    .presupuesto input[type="number"] {
        background-color: var(--light-grey) ;
        border-radius: 1rem;
        padding: 1rem;
        border: none;
        font-size: 2.2rem;
        text-align: center;
    }

    .presupuesto input[type="submit"] {
        background-color: var(--blue);
        border: none;
        padding: 1rem;
        text-align: center;
        font-size: 2rem;
        margin-top: 2rem;
        color: var(--white);
        font-weight: 900;
        width: 100%;
        transition: background-color ease 300ms;
    }

    .presupuesto input[type="submit"]:hover {
        cursor: pointer;
        background-color: #1048A4;
    }

    .alerta-enter-active, .alerta-leave-active {
        transition: opacity 2s;
    }
    .alerta-enter, .alerta-leave-to {
        opacity: 0;
    }
</style>