<template>
  <div>
    <p>basically a vue router sample, click below to relocate</p>
    <router-link to="/about"> about </router-link>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Footer",
});
</script>

<style scoped>
div {
  display: grid;
  place-items: center;
  position: absolute;
  top: 2rem;
  text-align: center;
  margin-bottom: 4rem;
}

div a {
  font-size: 1.3rem;
  margin-bottom: 3rem;
  text-transform: uppercase;
  font-weight: 700;
}
</style>
