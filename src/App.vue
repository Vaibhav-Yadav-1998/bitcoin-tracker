<template>
  <div id="app">
    <app-header />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader";

export default {
  name: "app",
  components: {
    "app-header": AppHeader
  }
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
