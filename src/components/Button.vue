<template>
  <button @click="onClick" :style="{ backgroundColor: bgColor }">
    {{ title }}
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Button",
  props: {
    title: String,
    bgColor: String,
  },
  methods: {
    onClick() {
      this.$emit("btn-click");
    },
  },
});
</script>

<style scoped>
button {
  border: 0px solid;
  padding: 0.5rem;
  color: white;
  cursor: pointer;
}
</style>
