<template>
    <div>
        <p>Version 1.0.0</p>
        <RouterLink to = "/">Back home</RouterLink>
    </div>
</template>



<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name : 'About'
    })
</script>

<style scoped>
    div {
        display: grid;
        place-items: center;
    }
</style>