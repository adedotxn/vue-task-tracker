<template>
    <div class="task-container" :key="task.id" v-for="task in tasks">
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" 
            @delete-task="$emit('delete-task', task.id)" 
            :task="task" /> 
    </div>
</template>


<script lang="ts">
import {defineComponent, type PropType} from 'vue'
import Task from './Task.vue'

interface TaskInterface {
    id : number, 
    text : string,
    day : string,
    reminder : boolean
}

export default defineComponent({
    name : "Tasks",
    components : {
        Task
    },
    props : {
        tasks : Array as PropType<TaskInterface[]>
    },
    emits : ['delete-task', 'toggle-reminder']
})

</script>

<style scoped>
</style>