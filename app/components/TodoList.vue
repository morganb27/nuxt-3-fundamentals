<script setup>
import { defineComponent, defineProps, ref } from '@vue/composition-api'
// We use Vanilla JS here!

defineProps({
    title : {
    type: String,
    default: 'Hello Hello!',
    required: true
    }
})


const todoList= ref([]);
const countCompleted = ref(0);
const countRemaining = ref(0);
        
function handleFetchTodoList() {
    fetch('https://jsonplaceholder.typicode.com/todos')
    .then(response => response.json())
    .then(data => {
        todoList.value = data
    console.log(data)
    countCompleted.value = countCompletedTasks(data);
    countRemaining.value = countRemainingTasks(data);
    })
}

function countCompletedTasks(data) {
    return data.filter(todo => todo.completed).length
}

function countRemainingTasks(data) {
    return data.filter(todo => todo.completed === false).length
}
</script>

<template>
    <div>
    <h1> {{ title }}</h1>
    <slot></slot>
    <h2>Here's the Todo List</h2>
    <img src="todo-image.avif" width="300" height="200"/>
    <button @click="handleFetchTodoList">Click Me</button>
    <p>Completed: {{ countCompleted }} | Remaining: {{ countRemaining }} </p>
    <ul class="todo-list">
        <li v-for="todo in todoList" :key="todo.id">
            <input type="checkbox" :checked="todo.completed"/>
            {{ todo.title }}
        </li>
    </ul>
    </div>
</template>

<style scoped>
    .todo-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
    }
</style>