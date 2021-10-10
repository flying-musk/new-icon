<template>
  <div id="app">
    <NewIcon />
  </div>
</template>

<script>
import NewIcon from './components/NewIcon.vue';
export default {
  name: 'App',
  components: { NewIcon },
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
