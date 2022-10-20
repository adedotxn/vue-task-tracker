<template>
  <header>
    <h1> {{title}}</h1>

    <div class="toggle">
      <Button 
        @btn-click="$emit('show-add-task')" 
        :title = "showAddTask ? 'Close' : 'Add Task' " 
        bgColor = "green" />
    </div>
  </header>
</template>

<script lang="ts">
  import Button from "./Button.vue"
  export default {
    name : "PageHeader",
    components : {
      Button,
    },
    props : {
      title : String,
      showAddTask : Boolean
    }, 
    emits : ["show-add-task"]
  }

  // import { ref } from "vue";

// const darkTheme = ref(false);

//   const toggleDarkMode = () => {
//     darkTheme.value = !darkTheme.value;
//   }
</script>

<style scoped>
header {
  /* line-height: 1.5;
  max-height: 100vh; */
  display: flex;
  justify-content: space-between;
  padding : .5rem;
}

header h1 {
  font-size: 1rem;
  color : white;
}

header div {
  /* border : 1px solid red; */
}

.toggle {
  display: flex;
  align-items: center;
  gap : .5rem;
}
@media (min-width: 1024px) {
  header {
    
  }

  .toggle {
    cursor: pointer;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
