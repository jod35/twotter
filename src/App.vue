<template>
    <div id="app">
      <UserProfile></UserProfile>
    </div>
</template>

<script>

import UserProfile from './components/UserProfile'
export default {
  name: 'App',
  components: {
   UserProfile
  },
}
</script>

<style>
#app {
  padding: 20px;
  margin: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background: lightblue;
}
</style>
