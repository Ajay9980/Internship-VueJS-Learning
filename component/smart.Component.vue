<!-- what the code does : - 
 this code is in Typescript  contains the logic with its types  , it perform addtodo , deletetodo and updateTodo. it uses slots for layout and a dumbComponent for rendering the data  -->


<script setup lang="ts">
import { reactive, ref } from 'vue';
import dumbComponent from './dumb.Component.vue';
import wrapper from './wrapper.vue';

interface Todo {
    id : Number,
    todo : String,
    done : Boolean
}

const todos = reactive<Todo[]>([])
const newTodo = ref<String>('')
let counterId = 0

function addTodo(){
    counterId++
    todos.push({
        id : counterId,
        todo : newTodo.value,
        done : false
    })
    newTodo.value = ''
}

function updateTodo(id : Number){
    const index = todos.findIndex(t => t.id === id)
    if (index !== -1)
    todos[index].done = !todos[index].done
}


function deleteTodo(id : Number){
    const index = todos.findIndex( t => t.id === id)
    if (index !== 1)
    todos.splice(index, 1)
}
</script>
<template>
    <div class="template-style">
        <!-- slot -->
        <wrapper>
            <!-- take input and add todo -->
            <div>
                <input  type="text"  v-model="newTodo">
                <br><br>
                <button :style="{width : '170px' , height : '50px' , borderRadius : '20px'}" @click="addTodo">add</button>
            </div>
            
            <!-- used slots layout -->
            <template #header>
                <h1 style="font-weight: 700;  font-family: Arial, Helvetica, sans-serif;"> Todo Lists</h1>
            </template>
            
            <!-- dumbComponent -->
            <dumbComponent v-for="(todo , index) in todos" :key="index" :id="todo.id"  :todo="todo.todo" :done="todo.done" @update="updateTodo" @delete="deleteTodo" />

            <!-- used slots layout -->
        <template #footer>
            <h1>Todo list ends here</h1>
        </template>
        
        
    </wrapper>
</div>

</template>
<style>
.template-style{
    font-size: x-large;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 10%;
}
</style>