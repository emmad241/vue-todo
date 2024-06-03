<template>
  <div id="app">
    <TodoComponent />
  </div>
</template>

<script>
import TodoComponent from './components/TodoComponent.vue';

export default {
  name: 'App',
  components: {
    TodoComponent
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background: #f9f9f9;
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  justify-content: center;
  min-height: 100vh;
  background-color: #dde6ed6e;
}
</style>
