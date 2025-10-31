<script>
    // TODO: Complete the code
    export default { 
        data() {
            return {
                
            }
        },
        // Hint: insert properties task (Object) and idx (Number)
        props:{
            task:Object,
            idx:Number
        },
        methods:{
            
        }, emits:[
            'removeTask'
    ]
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
       <div class="card" style="width:18rem">
        <img class="card-img-top" :src="imgLoc" alt="Card image">
        <div class="card-body">
            <h4 class="card-title">Deadline:{{ task.deadline }}</h4>
            <hr></hr>
            <p class="card-text">{{ task.desc }}</p>
            <button class="btn btn-primary" @click="$emit('removeTask',idx)">Done</button>
        </div>
        </div>

</template>


