<template>
  <div id="app">
    <UserProfile />
  </div>
</template>

<script>
import UserProfile from './components/UserProfile.vue';

export default {
  name: 'App',
  components: {
    UserProfile
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: aliceblue;
  min-height: 100vh;
}
</style>
