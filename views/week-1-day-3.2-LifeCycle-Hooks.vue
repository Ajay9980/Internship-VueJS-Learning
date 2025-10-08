<!-- 
What the code does:
This code demonstrates a simple Todo app with lifecycle management.
It allows users to add tasks, view total count, and toggle a child component
to observe lifecycle hooks like onMounted and onUnmounted in action.

Topics Covered:
 reactive() and ref() – for state management  
 computed() – to calculate total todos dynamically  
 watch() – to track reactive data changes  
 onMounted() and onUnmounted() – lifecycle hooks demonstration  
 v-if – to mount/unmount child component dynamically  
 Event handling and DOM updates
-->


<script setup>
import { computed, onMounted, onUnmounted, reactive, ref, watch } from 'vue';
import lifecycleComponent from '../component/lifecycleComponent.vue';
const todos = reactive([])
const newTodo = ref('')
 
function addTodo(){
    if(newTodo.value.length !== ''){
        todos.push(newTodo.value)
        newTodo.value = ''
    }
}

// Computed Hook to get length
const total = computed(()=>todos.length)


onMounted(()=>{
    console.log('Parent component is mounted ')
})

const show = ref(true)
 

let intervalId = setInterval(() => {
    console.log('Parent components interval is running.. ')
}, 10000);

onUnmounted(()=>{
    clearInterval(intervalId)
    console.log('interval is cleared from parent')
})



// watch() hook to track the value in newtodo
watch(newTodo,(newValue , oldValue)=>{
    console.log(`todo value changes from ${oldValue} to ${newValue}`)
})

</script>
<template>

<input type="text" v-model="newTodo"  >
 

<button @click="addTodo">Add</button>
<p>current todos length is : {{ total }}</p>

<lifecycleComponent v-if="show"/>
<button @click="show = !show">togglebutton</button>

<ul>
    <li v-for="(todo) in todos">{{ todo }}</li>
</ul>

</template>