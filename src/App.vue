<template>
  <PageHeader
    @show-add-task="handleAddTask"
    title="Task Trackerr"
    :showAddTask="showAddTask"
  />

  <router-view :showAddTask="showAddTask"></router-view>
  <footer>
    <Footer />
  </footer>
</template>

<script lang="ts">
import PageHeader from "./components/PageHeader.vue";
import Footer from "./components/Footer.vue";
import { defineComponent } from "vue";
export default defineComponent({
  name: "App",
  components: {
    PageHeader,
    Footer,
  },
  data() {
    return {
      showAddTask: false,
    };
  },
  methods: {
    handleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
});
</script>

<style scoped>
main,
footer {
  display: grid;
  place-items: center;
}
</style>
