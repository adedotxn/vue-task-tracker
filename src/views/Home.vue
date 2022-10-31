<template>
  <section v-if="showAddTask">
    <AddTask @add-task="addTask" />
  </section>

  <main>
    <Tasks
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </main>
</template>

<script lang="ts">
import Tasks from "../components/Tasks.vue";
import AddTask from "../components/AddTask.vue";
import { defineComponent } from "vue";
export default defineComponent({
  name: "Home",
  components: {
    Tasks,
    AddTask,
  },
  props: {
    showAddTask: Boolean,
  },
  data() {
    return {
      tasks: [
        {
          id: 0,
          text: "",
          day: "",
          reminder: false,
        },
      ],
    };
  },

  methods: {
    async addTask(task: {
      id: number;
      text: string;
      day: string;
      reminder: boolean;
    }) {
      const res = await fetch("http://localhost:5000/tasks", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(task),
      });

      const data = await res.json();
      this.tasks = [data, ...this.tasks];
    },

    async deleteTask(id: number) {
      if (confirm("Are you sure?")) {
        const res = await fetch(`http://localhost:5000/tasks/${id}`, {
          method: "DELETE",
        });

        if (res.status === 200) {
          this.tasks = this.tasks.filter((task) => task.id !== id);
        } else {
          alert("Error deleting file");
        }
      }
    },

    // used for marking a task as done or undone
    async toggleReminder(id: number) {
      const toToggle = await this.fetchTask(id);
      const update = { ...toToggle, reminder: !toToggle.reminder };

      const res = await fetch(`http://localhost:5000/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(update),
      });

      const data = await res.json();

      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    },

    async fetchTasks() {
      const response = await fetch("http://localhost:5000/tasks");

      const data = await response.json();

      return data;
    },

    async fetchTask(id: number) {
      const response = await fetch(`http://localhost:5000/tasks/${id}`);

      const data = await response.json();

      return data;
    },
  },

  async created() {
    this.tasks = await this.fetchTasks();
  },
});
</script>
