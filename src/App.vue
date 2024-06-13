<template>
  <div id="app" class="layout">
    <Layout />
  </div>
</template>

<script>
import Layout from './components/Layout.vue';

export default {
  name: 'App',
  components: {
    Layout,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
body {
  height: 100vh;
  margin: 0;
  font: 16px;
}

.layout{
width: 100%;
height: 100%;
}
</style>
