<template>
  <li class="list-group-item d-flex justify-content-between align-item-center">
      <span
        :class="{tachado: todo.estado}" 
        role="button" @click="realizada(todo.id)">
          {{todo.texto}}
      </span>
      <span role="button" @click="eliminar(todo.id)">
          <i  class="fas fa-times"></i>
      </span>
  </li>
</template>

<script>
import { inject } from 'vue'
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    setup() {
        const todos = inject('todos')

        const eliminar = id => {
            todos.value = todos.value.filter(item => item.id !== id)
        }

        const realizada = id => {
            todos.value = todos.value.map(item => {
                if(item.id === id){
                    item.estado = true
                }

                return item
            })
        }

        return {eliminar, realizada}
    }
}
</script>

<style>
.tachado {
    text-decoration: line-through;
}
</style>