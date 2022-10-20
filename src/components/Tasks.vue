<template>
    <div class="task-container" :key="task.id" v-for="task in tasks">
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" 
            @delete-task="$emit('delete-task', task.id)" 
            :task="task" /> 
    </div>
</template>


<script lang="ts">
import Task from './Task.vue'

export default {
    name : "Tasks",
    components : {
        Task
    },
    props : {
        tasks : Array
    },
    emits : ['delete-task', 'toggle-reminder']
}

</script>

<style scoped>
    .task-container {
       
    }
</style>