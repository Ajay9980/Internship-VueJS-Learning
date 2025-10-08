<!-- 
what the code does:
This component demonstrates Vue's lifecycle hooks — specifically `onMounted` and `onUnmounted`.
It starts an interval when the component mounts and clears it automatically when unmounted.
Used along with a parent toggle to observe lifecycle behavior in real-time.

Topics Covered:
 onMounted() – runs code when component is created and added to DOM  
 onUnmounted() – cleans up (like clearing intervals) when component is destroyed  
 setInterval() – for simulating background tasks or periodic updates  
 Lifecycle cleanup – avoiding memory leaks and unnecessary background work
-->

<script setup>
import { onMounted, onUnmounted } from 'vue'

onMounted(()=>{
    console.log('Child Component Mounted')
})

let intervalId = setInterval(() => {
    console.log('Child Component interval is running....')
}, 10000);

onUnmounted(()=>{
    clearInterval(intervalId)
    console.log('clearing the interval from child')
})
</script>

<template>
  <h3>Child component is active</h3>
</template>
