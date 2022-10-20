<template>
    <section @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'done' : 'undone' ,'task_wrapper']">
        <div class="task">
            <h3>{{task.text}}</h3>
            <p>{{task.day}}</p>
        </div>

        <div @click="onDelete(task.id)" class="remove">
            <h3>Remove Task</h3>
        </div>
    </section>
</template>


<script lang="ts">

export default {
    name  : "Task",
    props : {
        task : Object
    },
    methods : {
        onDelete(id : number) : void {
            this.$emit('delete-task', id)
        }
    }
}
</script>


<style scoped>

.task_wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1rem;
    border : 1px solid white;
    width :90vw;
    padding : .5rem 1rem;
}

.done {
    background-color: rgba(0, 128, 0, 0.36);
}

.undone {
    background-color: black;
}

.task h3 {
    color : white
}

.remove {
    cursor: pointer;
    border : 1px solid grey;
    padding  : .2rem .5rem;
}
</style>