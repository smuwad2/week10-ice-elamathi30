<!-- <script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props:{
            subject:String,
            entry: String,
            mood: String, 
        },
        computed:{
            imgLoc(){
                //use the string literal left side of keyboard 
                return `/assests/${this.mood.toLowerCase()}.png` 
                //vue will know search under the public folder for assests 

            }
        }
    }
</script>


<template>
    <!-- TODO: add your template code here. Use boostrap card --> 
     <!-- copied over from the w3 card layout  -->
        <!-- <div class="card" style="width:18rem">
        <img class="card-img-top" :src="imgLoc" alt="Card image">
        <div class="card-body">
            <h4 class="card-title">{{ subject }}</h4>
            <p class="card-text">{{ entry }}</p>
        </div>
        </div> -->
<!-- 
</template> --> -->

<script>
export default {
  props: {
    subject: String,
    entry: String,
    mood: String
  },
  computed: {
    imgLoc() {
      // only return image if mood exists
      return this.mood ? `/assets/${this.mood.toLowerCase()}.png` : '';
    }
  }
}
</script>

<template>
  <div class="card" style="width: 18rem; margin-bottom: 1rem;">
    <!-- only show image if imgLoc exists -->
    <img v-if="imgLoc" class="card-img-top" :src="imgLoc" :alt="mood + ' image'">
    <div class="card-body">
      <h4 class="card-title">{{ subject }}</h4>
      <p class="card-text">{{ entry }}</p>
    </div>
  </div>
</template>
