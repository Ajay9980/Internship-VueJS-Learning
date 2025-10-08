<!-- 
What this code does:
This code defines a reusable custom input component that supports v-model binding with the parent component.
It allows passing a label, input type, and handles two-way data flow between parent and child.

Topics Covered:
- defineProps() for receiving props from parent
- defineEmits() for sending data updates to parent
- v-model binding in custom components
- Event emission using $emit
- Template binding with :value and @input
-->


<script setup>

defineProps({
    modelValue : String,
    label : String,
    type : {type : String , default : 'text'}
     
})

defineEmits(['update:modelValue']);

</script>
<template>

<h1>{{ label }}</h1>

<input :type="type" :value="modelValue"  @input="$emit('update:modelValue', $event.target.value)" >
</template>