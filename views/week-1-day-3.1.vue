<script setup>
import CustomInput from '../component/MyInput.vue'
import NewInput from '../component/CustomInput.vue'
import Counter from '../component/Counter.vue';
import { computed, reactive, ref } from 'vue';
const username = ref('')

const value = ref('low')
const subscription = ref('free')
const flavours = ref([])
const textInput = ref('')
const title = ref('')
const text = ref('')

const tasks = reactive([{task : 'eat lunch' , done : false} , {task :'eat dinner' , done : false} , {task:'sing a song' , done : false} ])
const newtask = ref('')

function addTask(){
    tasks.push({task : newtask , done : false})
}

const sort = ref('all')
const filteredTask = computed(()=>{
    if(sort.value === 'pending'){
        return tasks.filter((task)=> task.done === false)
    }else if (sort.value === 'completed'){
        return tasks.filter((task)=> task.done === true)
    }else{
        return tasks
    }
})

const count = ref(0)
function add(){
    count.value += 1
}

</script>
<template >
 
 <div  :class="{'top-elem' : true}">

 
<input type="text" v-model="newtask">
<br>
<button @click="addTask">add Task</button>
<br>
<h1> Todays Todo List</h1>

<button @click="sort='pending'">Show pending</button>
<button @click="sort='completed'">Show completed</button>
<button @click="sort='all'">Show all</button>

<ul>
    <li v-for="(task,index) in filteredTask">{{ task.task}} || {{ task.done ? 'completed' : 'Pending' }} <input type="checkbox" @click="task.done = !task.done"></li>
</ul>


<br>




 priority :- <label >
    <input type="radio" value="low" v-model="value">
    Low
 </label>
 <label>
    <input type="radio" value="high" v-model="value">
    High
 </label>

<br>
{{ value }}
<br>
<br><br>
<label>
    <input type="checkbox" value="strawberry" v-model="flavours">
    strawberry
</label>
<label>
    <input type="checkbox" value="choclate" v-model="flavours">
    choclate
</label>
<label>
    <input type="checkbox" value="vanilla" v-model="flavours">
    vanilla
</label>

{{ flavours }}


<br>
<br><br>
<select v-model="subscription">
    <option value="free">Free</option>
    <option value="standard">Standard</option>
    <option value="Pro">Pro</option>
</select>
<br>
{{ subscription }}
<br><br><br>

<input type="text" v-model="textInput">
<br>
{{ textInput }}

 </div>


 <div>
    <h1>custom component</h1>
    <CustomInput type="text" v-model="title" />
    <h1>{{ title }}</h1>
 </div>

 <div>
    <h1>new input</h1>
   <NewInput v-model="text"  /> 
 </div>
 {{ text }}

 <br>
 <div>
<Counter  @sayHello="add"/>
<br>
<p>count :- {{ count }}</p>
 </div>
</template>

<style>

.top-elem{
    font-size: x-large;
    margin-left: auto;
}
</style>