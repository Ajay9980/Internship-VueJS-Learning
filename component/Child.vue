<script setup>

defineProps({
    label : String,
    modelValue : String,
    type : {type : String , default : 'text'} 
})

defineEmits(['update:modelValue'])

</script>
<template>


<h1>{{ label }}</h1>
<input :type="type"  @input="$emit('update:modelValue', $event.target.value)" >
 
</template>