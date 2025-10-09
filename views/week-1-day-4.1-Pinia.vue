<script setup>
import { useCounterStore } from '../store/counter';
import Counter from '../component/Counter.vue';

// using pinia store
const  Store = useCounterStore()


</script>
<template>
    <div class="top-elem">

        <div>
            {{ Store.count }}
        </div>
        <div  style="display: flex; gap: 20%;">


            <button style="width:2cm; height: 1cm; font-size: x-large; border-radius: '20px';"  @click="Store.increment">+</button>

            <button style="width:2cm; height: 1cm; font-size: x-large; border-radius: '20px';"  @click="Store.decrement">-</button>
            
        </div>
         <div>
            <!-- Child components with passign any props using the pinia store -->
            <Counter/>
         </div>
    </div>
</template>
<style>

.top-elem{
    font-size :500%;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 700;
    display: flex;
    align-items: center;
    margin-top: 20%;
}

</style>