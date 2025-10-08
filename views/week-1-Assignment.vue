<!-- created a Todo List , it can perform add task , sort task on the basis of pending or completed -->

<script setup>
import { computed, ref , reactive } from 'vue';

const tasks = reactive([
  { task: "Finish Vue project", completed: false },
  { task: "Review pull requests", completed: true },
  { task: "Prepare for team meeting", completed: false },
  { task: "Update documentation", completed: true },
  { task: "Fix login page bug", completed: false },
  { task: "Test API integration", completed: true },
  { task: "Plan next sprint", completed: false }
]);


const sort = ref('all')

const filteredTasks = computed(()=>{
    if (sort.value === 'pending'){   
        return tasks.filter((task)=> task.completed === false)
    }else if (sort.value === 'completed'){
        return tasks.filter((task)=>task.completed === true)
    }else{
        return tasks
    }
})

const newtask = ref('')

function addTask(){
    tasks.push({
        task : newtask,
        completed : false
    })
}

</script>
<template >
 <div :class="{'top-elem' : true}"> 
<h1 :style="{fontSize : '20px' , fontFamily:'cursive' , fontWeight : 'bold'}">List Of Todays Tasks</h1>

<input type="text" v-model="newtask">
<br>
<button @click="addTask">Add Task</button>
<div>
    <button @click="sort='pending'">show Pending</button>{{ "    " }}
    <button @click="sort='all'">show All</button>{{ "    " }}
    <button @click="sort='completed'">show Completed</button>
    
</div>
<div>
    <h1 v-if="sort==='pending'">list of Pending Tasks</h1>
    <h1 v-else-if="sort==='completed'">list of Completed Tasks</h1>
    <h1 v-else>list of All Tasks</h1>
</div>
<ul>
    <li v-for="(task,index) in filteredTasks"   :key="index">{{ task.task }}{{ "  " }} || {{ task.completed === true ? 'Completed' : 'Pending' }}
        <button @click="task.completed = !task.completed">Done</button></li>
</ul>
</div>
</template>

<style>
 .top-elem{
    font-size: x-large;
    display: flex;
    flex-direction: column;
    justify-items: center;
    align-items: center;
    gap: '10px';

 }
</style>