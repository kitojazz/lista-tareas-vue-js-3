<template>
    <ul class="list-group">
        <todo-item 
            v-for="todo in todos" :key="todo.id"
            :todo="todo"
        />

        <li v-if="todos.length === 0"
            class="list-group-item"
        >
            No hay elementos
        </li>

        <todo-footer v-if="todos.length != 0"
        />

        <todo-filtros />

    </ul>
</template>

<script>
import { computed, inject, provide, ref } from 'vue'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltros from './TodoFiltros.vue'
export default {
  components: { TodoItem, TodoFooter, TodoFiltros },

  setup() {
    TodoFooter
      const todosTodos = inject('todos')

      const estado = ref('all')

      const todos = computed(() => {
          if (estado.value === 'all') {
            return todosTodos.value
          }

          if (estado.value === 'activos') {
              return todosTodos.value.filter(item => item.estado === false)
          }

          if (estado.value === 'completados') {
              return todosTodos.value.filter(item => item.estado === true)
          }
          
      })
      //proporciona las props a todos sus hijos pero no sirve para el todoApp que es el padre de todoList
      provide('estado', estado)
      return {todos}
  }

}
</script>

<style>

</style>