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

    <div class="twoots">
        <h3 class="twootes-header">
            Recent Twoots
        </h3>

        <div class="twoot" v-for="twoot in twoots" v-bind:key="twoot.id">
            <Twoot  v-bind:twoot="twoot" 
                    v-bind:content="twoot.content" 
                    v-bind:username="user.username"
                    v-on:favorite="toggleFavorite(twoot.id)">
            </Twoot>            
        </div>
    </div>
</template>

<script>

import Twoot from './Twoot'

export default {
        name:"UserProfile",
        components:{Twoot},
        data() {
            return {
                user:{
                    username:"jod35",
                    firstName:"ssali",
                    lastName:"Jonathan",
                    email:"jodestrevin@gmail.com",
                    isAdmin:false,
                    followers:0
                },
                twoots:[
                    {id:1,
                    content:"Twotter is cool",
                    },
                     {id:2,
                    content:"I am coding Vue",
                    },
                     {id:3,
                    content:"This is amazing",
                    },
                ]
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
            },
            toggleFavorite(id){
                console.log(`Favorited twoot with ID ${id}`);
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
        },
        

    }

</script>

<style>
.user{
    background-color: white;
    padding: 20px;
    width: 20%;
    height: 400px;
    border-radius: 7px;
}
.twoots{
    width: 70%;
    padding: 20px;
}
.twoot{
    padding: 10px;
    border-radius: 7px;
    background-color: white;
    margin: 10px;
    transition: all 1.2s;
}
.twoot:hover{
    transform: scale(1.1,1.1);
    cursor: pointer;
}
.admin-badge{
    background-color: rebeccapurple;
    color: white;
    padding: 10px;
    
}
</style>