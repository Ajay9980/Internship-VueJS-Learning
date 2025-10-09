<!-- what the code does : - this is the child component created in typescript akes the start and steps from parent and then perform Increment/decrement and double using computed -->

<script setup lang="ts">
import { computed, ref } from 'vue';

interface Props {
    starts : number,
    steps : number
}
const props = defineProps<Props>()

const emit = defineEmits<{(e : 'update' , value : number)}>()
const count = ref(props.starts ?? 0)

function increment(){
    count.value += props.steps ?? 0
    emit('update' , count.value)
}

const double = computed(()=>count.value * 2)

function reset(){
    count.value = props.starts ?? 0
}

</script>
<template>

 <h1>Counter</h1>
 <hr>
 
 <h1>Child Count : {{ count }}</h1>
<br> <h1>Double : {{ double }}</h1>
 <br><button @click="increment">Increment</button>
 <br><button  @click="reset">Reset</button>
</template>