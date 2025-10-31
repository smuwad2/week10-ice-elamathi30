<!-- <script>
    // Import BlogPost component
    import blogPost from './subcomponents/BlogPost.vue'
	import axios from 'axios'
    export default {
        data() {
            return {
                posts: [] // array of post objects from the database 
            }  
        },
        components:{
            blogPost
        },
        computed: {
            baseUrl() {
                if (window.location.hostname=='localhost')
                    return 'http://localhost:3000' 
                else {
                    const codespace_host = window.location.hostname.replace('5173', '3000')
                    return `https://${codespace_host}`;
                }
            }
        },
        created() { // created is a hook that executes as soon as Vue instance is created
            axios.get(`${this.baseUrl}/posts`)
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        }
    }
</script>



<!-- <template>
   <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <!-- <blog-post v-for="post in posts"  -->
    <!-- :subject="post.subject" 
    :entry="post.entry" 
    :mood="post.mood" 
    :key="post.id">
    </blog-post> 
</template>  --> -->
 -->


<script>
import BlogPost from './subcomponents/BlogPost.vue'
import axios from 'axios'

export default {
  components: { BlogPost },
  data() {
    return {
      posts: []
    }
  },
  computed: {
    baseUrl() {
      if (window.location.hostname === 'localhost') {
        return 'http://localhost:3000'
      } else {
        const codespace_host = window.location.hostname.replace('5173', '3000')
        return `https://${codespace_host}`
      }
    }
  },
  created() {
    axios.get(`${this.baseUrl}/posts`)
      .then(response => {
        // keep posts as returned by API
        this.posts = response.data.map((post, index) => ({
          id: post.id ?? index,
          subject: post.subject ?? '',
          entry: post.entry ?? '',
          mood: post.mood // keep undefined if missing
        }))
      })
      .catch(error => {
        this.posts = [{
          id: 0,
          subject: 'Error',
          entry: 'There was an error: ' + error.message,
          mood: undefined
        }]
      })
  }
}
</script>

<template>
  <div>
    <!-- vertical list of posts -->
    <BlogPost
      v-for="post in posts"
      :key="post.id"
      :subject="post.subject"
      :entry="post.entry"
      :mood="post.mood"
    />
  </div>
</template>


