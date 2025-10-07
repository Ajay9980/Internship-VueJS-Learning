<script setup>
import { ref } from 'vue';
import Child from '../component/Child.vue';

const username = ref('')
const password = ref('')
const submitted = ref(false)


function handleSubmit(){
    submitted.value = !submitted.value
    alert(username.value , password.value)
}
</script>
<template>

    <Child  v-model="username" type="text" label="Username"/>
    <Child v-model="password" type="password" label="Password"/>

    <button @click="handleSubmit">Submit</button>

    <p v-if="submitted === true" >username : {{ username }} , password : {{ password }}</p>

</template>