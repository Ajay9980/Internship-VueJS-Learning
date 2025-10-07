<script setup>
defineProps(['modelValue'])
</script>
<template>
    <input :value="modelValue"  @input="$emit('update:modelValue', $event.target.value)">
</template>