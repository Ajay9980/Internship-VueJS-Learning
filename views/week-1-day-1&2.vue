<!-- 
Topics :- reactive() and ref() , computed() , class and inline styles , event handlers (@click , @input ) , modifiers ( .Prevent) , Conditional Rendering (v-if , v-else-if , v-else) , v-for (for loop).
 -->


<!-- 
Statement : - In this there is a list of students with name , task and completed with boolean  in which it can add students and can toggle the completed , can sort and list students between completed , pending and all 
 -->



<!-- SCF (Single Component File) -->
<script setup>
import { computed, reactive, ref } from 'vue';

// used reactive state 'reactive()' for non-primitive (Object)
const students = reactive([
  { name: 'Ajay', task: 'Finish Vue notes', completed: false },
  { name: 'Ganesh', task: 'Practice ref() and reactive()', completed: true },
  { name: 'Rohit', task: 'Build mini Vue project', completed: false }
])

// used reactive state 'ref()'  for primitives
const newStudent = ref('')
const newTask = ref('')
const showCompleted = ref('all')


function newStudentAdd(event){
    newStudent.value = event.target.value

}

function newTaskAdd(event){
    newTask.value = event.target.value
}

const filteredStudent = computed(()=>{
    // accessed variable data  using '.value'
    if (showCompleted.value === 'pending'){
        return students.filter((student)=>student.completed === false)
    }else if(showCompleted.value === 'completed'){
        return students.filter((student)=>student.completed === true)
    }else{
        return students
    }

    
})

function addStudent(){
    students.push({name : newStudent.value,
        task : newTask.value,
        completed : false
    })
}
  

 
</script>

<template  >
<!-- class binding used class 'top-elem' class  -->
<div  :class="{'top-elem' : true}">

    <h1>Student Name</h1>
    <!-- used inline style  -->
    <input :style="{ border : '20%', borderColor : 'black', padding : '5px' , fontSize : '30px'}" type="text" @input="newStudentAdd">
    <!-- used '@input' for  extracting of student name -->
    
    <h1>Task</h1>
    
    <!-- used inline style  -->
    <input :style="{ border : '20%' , padding : '5px' , fontSize : '20px', marginBottom : '20px'  }"  @input="newTaskAdd">
    <!-- used '@input' for extracting of task -->

<button :style="{width : '100px' , color : 'white' , backgroundColor : 'black' , border : '50 px'}" @click.prevent="addStudent">Add Student</button> <!-- used modifiers '.prevent'  -->

<div>
    <!-- used event handlers '@click or v-on' -->
    <button @click="showCompleted = 'all'">Show all </button>
    <button @click="showCompleted = 'pending'">Show only Pending </button>
    <button @click="showCompleted = 'completed'">Show only completed </button>

</div>

<!-- used conditional rendering of text using 'v-if', 'v-else-if' , 'v-else' -->
<h1 v-if="showCompleted === 'pending'">List of all pending Task!</h1>
<h1 v-else-if="showCompleted === 'completed'">List of all Completed Task</h1>
<h1 v-else>List of all Tasks</h1>



<ul>
    <h1>Student List</h1>
   <!-- used 'v-for' to create list of students -->
    <li v-for="(student,index) in filteredStudent"   :key="index">Name :{{ student.name }} | Task : {{ student.task }} | Completed :

        <span> {{ student.completed  }}</span>
        
        <!-- used event handlers '@click' -->
        <button @click="student.completed = !student.completed">Done</button>
    </li>
</ul>

</div>

</template>

<style scoped>

.top-elem {
    display: flex;
    flex-direction: column;
    justify-content: center;
    justify-items: center;
    margin-left: 20%;
    margin-right: 20%;

}
</style>
