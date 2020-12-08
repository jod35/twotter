<template>
    <div id="app">
        <h2>@{{user.username}}</h2>
        <p>{{getFirstName}}</p>
        <p>{{user.email}}</p>
        <p>IsAdmin: {{user.isAdmin}}</p>
        <strong>{{user.followers}} followers</strong>
        <br>
        <br>
        <button v-on:click="follow()">Follow</button>
    </div>
</template>

<script>


export default {
  name: 'App',
  components: {
   
  },
  data(){
    return {
       followers:0,
       user:{
          id:1,
          username:'_jod35',
          firstName:'JOnathan',
          lastName:'Ssali',
          email:'jodestrevin@gmail.com',
          isAdmin:true,
          followers:0
        }
    }
  },
  computed:{
    getFirstName(){
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods:{
    follow(){
      return this.user.followers++;
    }
  },
  mounted(){
    this.follow();
  },
  watch:{
    followers(newFollowerCount,oldFollowerCount){
       if (newFollowerCount > oldFollowerCount){
         console.log(`${this.firstName} has gained a follower`);
       }
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
