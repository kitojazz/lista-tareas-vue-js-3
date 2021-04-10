<template>
    <div class="card mt-3">

        <div class="card-body d-flex justify-content-between">
            <span 
                role="button"
                @click="filtrar('activos')">
                Activos
            </span>
            <span 
                role="button"
                @click="filtrar('all')">
                todos
            </span>
            <span 
                role="button"
                @click="filtrar('completados')">
                Completados
            </span>
        </div>
    </div>
</template>

<script>
import { inject } from 'vue'
export default {
    setup() {
        const estado = inject('estado')

        const filtrar = valor => {
            estado.value = valor
        }
      

        return {
            filtrar
        }
    }
}
</script>

<style>

</style>