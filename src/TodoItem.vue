<!-- 
 Renders each Todo item
 
 Takes todo as a string param for the todo's description
 Takes deleteFn as function to handle removing of item from the list of todos
-->
<script setup>
defineProps({
    todo: { type: String, required: true },
    deleteFn: { type: Function, default: () => {} },
});
</script>

<template>
    <li>
        <span>{{ todo }}</span>
        <!-- This button will help individually remove todo items! -->
        <!-- Create an anonymous function that does nothing in the event that deleteFn is undefined -->
        <button @click="deleteFn()">Delete</button>
    </li>
</template>
