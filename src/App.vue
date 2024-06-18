<script setup>
import { ref } from "vue";

const input = ref("");
const todos = ref([]);
const isShow = ref(true);

// Add a new todo to the list of todos
function prependTodo() {
    todos.value = [input.value, ...todos.value];
}

// Remove the unwanted todo from todos based on index
function remove(index) {
    todos.value.splice(index, 1);
}
</script>

<template>
    <div>
        <!-- Handles insertion of todos -->
        <input v-model="input" />
        <!-- <input :value="input" @input="(event) => (text = event.target.value)" /> -->

        <button @click="prependTodo">Submit</button>
        <!-- Show list of todos -->
        <h2>Todos</h2>
        <!-- Can be toggled to not show all todos! -->
        <input v-model="isShow" type="checkbox" />
        <span>Show Todos</span>
        <!-- Renders the todo list if isShow is true -->
        <ul v-if="isShow">
            <!-- Render each todo as a list item -->
            <li v-for="(todo, index) in todos">
                <span>{{ todo }}</span>
                <!-- This button will help individually remove todo items! -->
                <button @click="remove(index)">Delete</button>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
}
.logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
