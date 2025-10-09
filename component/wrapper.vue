<!-- what the code does : - it gives layouts to the smartComponent -->

<script setup lang="ts">

</script>
<template>

    <div class="card-header">
        <slot name="header"></slot>
    </div>

    <div>
        <slot></slot>
    </div>

    <div class="card-footer">
        <slot name="footer"></slot>
    </div>
</template>