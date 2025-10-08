<!-- what this code does : this is the child component which create slots for parent components . basic , named and scoped slots -->
<script setup>

const extraInfo = {likes : 1200 , comments : 200}

</script>
<template>
 
 <!-- named slots -->
    <div class="card-header">
     <slot name="header"></slot>
    </div>
<!-- named slots -->


<!-- basic slots -->
<main>
    <slot></slot>
</main>
<!-- basic slots -->




<!-- named slots -->
<div class="card-footer">
    <slot name="footer"></slot>
</div>
<!-- named slots -->


<!-- scoped slots ( providing data to parent component) -->
<div class="extra-info">
    <slot name="extra"  :info="extraInfo"></slot>
</div>
<!-- scoped slots -->

</template>