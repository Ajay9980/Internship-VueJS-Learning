<!-- what the code does : - created a simple input which is binded to the count variable in pinia store in counter.js , removes the effort of props drilling or props  passing  -->

<script setup>
import { useCounterStore } from '../store/counter';

const Store = useCounterStore()
</script>
<template>
    <input style="font-size: xx-large;" type="number" v-model="Store.count">
</template>