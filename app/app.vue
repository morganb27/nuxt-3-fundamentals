<script>
import { defineComponent } from '@vue/composition-api'
import TodoList from './components/TodoList.vue'

export default defineComponent({
  components: { TodoList },
  setup() {
    
  },
})
</script>

<template>
  <div>
    <h1>Hello Front End Masters!</h1>
    <TodoList />
  </div>
</template>
