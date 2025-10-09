<!-- 
What this code does:
This code demonstrates two-way data binding between a parent and a custom child component using v-model.
It takes a username and password input from the user and displays them after submission with an alert.

Topics Covered:
- Ref() for reactive data
- Custom component with v-model
- Event handling using @click
- Data binding and displaying values
-->

<script setup lang="ts">
import { ref } from 'vue';
import Child from '../component/Child.vue';


const username = ref('')
const password = ref('')


function submit(){
alert(`username : ${username.value} and password : ${password.value}`)
}

</script>
<template>

<Child type="text" label="Username" v-model="username"  />

<Child type="password" label="password" v-model="password"/>
<br>

<button  @click="submit">Submit</button>
    <div>
    username :  {{ username }}
    password : {{ password }}
    </div>
</template>