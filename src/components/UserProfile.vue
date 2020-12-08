<template>
    <div class="user">
        <h2 class="username">
            @{{user.username}}
        </h2>
        <p>{{user.getfullName}}</p>
        <p ></p>
        <p>{{user.email}}</p>
        <p class="admin-badge" v-if="user.isAdmin">{{user.isAdmin}}</p>
        <strong>
            {{user.followers}} followers
        </strong>
        <br>
        <button @click="followUser()">Follow</button>
    </div>
</template>

<script>
export default {
        name:"UserProfile",
        data() {
            return {
                user:{
                    username:"jod35",
                    firstName:"ssali",
                    lastName:"Jonathan",
                    email:"jodestrevin@gmail.com",
                    isAdmin:false,
                    followers:0
                }
            }
        },
        computed:{
            getfullName(){
                return `${this.user.firstName} ${this.user.lastName}`
            }
        },
        methods:{
            followUser(){
                this.user.followers++;
            }
        },
        mounted(){
            this.followUser();
        },
        watch:{
            follow(oldFollwerCount , NewfollowerCount){
                if(oldFollwerCount< NewfollowerCount){
                    console.log(`${this.user.username} has been followed`);
                }
            }
        }

    }

</script>

<style>
.user{
    background-color: white;
    padding: 20px;
        width: 40%;
}
    .admin-badge{
        background-color: rebeccapurple;
        color: white;
        padding: 10px;
        
    }
</style>