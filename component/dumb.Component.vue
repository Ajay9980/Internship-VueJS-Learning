<!-- what the code does :- this code is in typescript only for ui rendering purpose take the props with types and perform emits with types  -->

<script setup lang="ts"> 

interface Todo {
    id : Number,
    todo : String,
    done : Boolean
}

const props = defineProps<Todo>()
const emit = defineEmits<{
(e : 'update' , value : Number)
(e : 'delete' , value : Number)
}>()

function toggleTodo(){
    emit('update', props.id)
}

function deleteTodo(){
    emit('delete' , props.id)
}


</script>
<template >
    <div >
        <input type="checkbox" @change="toggleTodo">
        <span>{{ todo }}</span>||<span>{{ done ? 'Done' : 'undone' }}</span>||
        <button @click="deleteTodo">delete</button>
    </div>
    </template>
    
<style>
 
</style>