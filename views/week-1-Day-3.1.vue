<!-- what this code does : this code covers the topic of slots , basic slots , named slots and scoped slots -->

<script setup>
import Card from '../component/Card.vue';


</script>
<template> 

<Card>

    <!-- Named Slots -->
    <template #header>
        <p>This is the  header content from parent</p>
    </template>
    <!-- Named Slots -->
    
    
    <!-- Basic Slots (Default slots) -->
    <p>This the main body from parent</p>
    <!-- Basic Slots -->
    
    
    <!-- Named Slots -->
    <template #footer>
        <p>This is the footer from parent</p>
    </template>
    <!-- Named Slots -->


    <!-- Scoped slots ( Can use Childs Data ) -->
    <template #extra="{info}">
        <p>Likes : {{ info.likes }} , Comments : {{ info.comments }}</p>
    </template>
    <!-- Scoped slots -->
</Card>

</template>