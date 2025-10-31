<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props:{
            subject:String,
            entry:String, 
            mood:String
        }
    }
</script>


<template>
    <!-- TODO: add your template code here Use boostrap card --> 
        <div class="card" style="width:18rem">
        <img class="card-img-top" :src="imgLoc" alt="Card image">
        <div class="card-body">
            <h4 class="card-title">{{ subject }}</h4>
            <p class="card-text">{{ entry }}</p>
        </div>
        <!-- only difference from the blogpost 1 is the slot here -->
        <slot></slot>
        </div>

</template>

