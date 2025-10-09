<!-- what the code does :- created normal couter code using Typescript which give start and steps for count  -->
<script setup lang="ts">
import { ref } from 'vue';
import counterTs from '../component/counter-ts.vue';

const parentcount = ref(0)

function attachCount(newCount : number){
    parentcount.value =  newCount
}
 
</script>
<template>
<counterTs :starts="2" :steps="3" @update="attachCount"/>
  <div>
    parent count :- {{ parentcount }}
  </div>
</template>