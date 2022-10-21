<script lang="ts">
import PageHeader from "./components/PageHeader.vue";
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'
import {defineComponent} from 'vue'
export default defineComponent({
  name : "App",
  components : {
    PageHeader,
    Tasks,

    AddTask
  },
  data() {
    return {
      tasks : [{
        id : 0,
        text : "",
        day : "",
        reminder : false
      }],
      showAddTask : false
    }
  },
  methods : {
    deleteTask(id :  number) {
      if(confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id : number) {
      this.tasks = this.tasks.map((task) => 
        task.id === id ? {...task, reminder : !task.reminder} : task
      )
    },
    addTask(task: { id: number; text: string; day: string; reminder: boolean; }) {
      this.tasks = [task, ...this.tasks]
    },
    handleAddTask() {
      this.showAddTask = !this.showAddTask
    }
  },
  created() {
    this.tasks = [
      {
        id : 1,
        text : "Doctor's Appointment",
        day : "Dec 31",
        reminder : true
      },
      {
        id : 2,
        text : "Tattoo Appointment",
        day : "Dec 31",
        reminder : true
      }, {
        id : 3,
        text : "Golf Practice",
        day : "Dec 31",
        reminder : true
      },
      {
        id : 4,
        text : "Wake up",
        day : "Dec 31",
        reminder : false
      },
    ]
  }
})
</script>

<template>
  <PageHeader 
    @show-add-task="handleAddTask" 
    title = "Task Trackerr" 
    :showAddTask = "showAddTask"
  />

  <section v-if="showAddTask">
    <AddTask @add-task ="addTask" />
  </section>

  <main>
    <Tasks :tasks="tasks" 
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </main>
  
</template>

<style scoped>
  main {
    display: grid;
    place-items: center;
  }
</style>
