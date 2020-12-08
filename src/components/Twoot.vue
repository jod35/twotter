<template>
    <div>
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

}
</script>

