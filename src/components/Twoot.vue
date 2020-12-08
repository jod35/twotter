<template>
    <div v-on:click="favoriteTwoot(twootId)">
        <h4>@{{username}}</h4>
        <p>{{twoot.content}}</p>
    </div>
</template>

<script>
export default {
    name:"Twoot",
    props:{
        username:{
            type:String,
            required:true
        },
        twoot:{
            type:Object,
            required:true
        }
    },
    methods:{
        favoriteTwoot(id){
            this.$emit('favorite',id);
        }
    }

}
</script>

