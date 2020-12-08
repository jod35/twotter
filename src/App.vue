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
body{
  padding: 0;
  margin: 0;
}
#app {
  width:100%;
  min-height: 100vh;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  margin: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background: lightblue;
}
</style>
