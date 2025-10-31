<script setup>
    // Import BlogPost component
    import blogPost from './subcomponents/BlogPost2.vue'
	import axios from 'axios'
</script>

<!-- <script>
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        components:{
            blogPost
        },
        computed: {
            baseUrl() {
                if (window.location.hostname == 'localhost')
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
        },
        // methods: {
        //     deletePost(id) {
        //         // TODO: Complete the delete method
        //         //not the right way to delete post
        //         // posts.remove(id) 
        //         // axios.get(`http://localhost:3000/deletePost`,
        //         // params{
        //         //     id: id
        //         // }
        //         axios.get(`${this.baseUrl}/deletePost`,
        //             {
        //                 params: {
        //                     id: id
        //                 }
        //             }
        //         )
        //         .then(response => {
        //             console.log(response.data)
        //             //to show the updated posts on the webpage 
        //             this.posts = this.posts.filter(post => post.id!=id)

        //         }).catch(error => {
        //             this.posts = [{ entry: 'There was an error: ' + error.message }]
        //     })
        //     }}
        methods: {
            deletePost(id) {
                axios.get(`${this.baseUrl}/deletePost`, {
                params: {
                    id: id
                }
                })
    .then(response => {
      console.log(response.data)
      // update the list of posts
      this.posts = this.posts.filter(post => post.id != id)
    })
    .catch(error => {
      this.posts = [{ entry: 'There was an error: ' + error.message }]
    }) // 
  }
}
    }
</script> -->
<script>
export default {
  data() {
    return {
      posts: [] // array of post objects
    }
  },
  components: {
    blogPost
  },
  computed: {
    baseUrl() {
      if (window.location.hostname == 'localhost')
        return 'http://localhost:3000'
      else {
        const codespace_host = window.location.hostname.replace('5173', '3000')
        return `https://${codespace_host}`
      }
    }
  },
  created() {
    axios.get(`${this.baseUrl}/posts`)
      .then(response => {
        this.posts = response.data
        console.log(response.data)
      })
      .catch(error => {
        this.posts = [{ entry: 'There was an error: ' + error.message }]
      })
  },
  methods: {
    deletePost(id) {
      axios.get(`${this.baseUrl}/deletePost`, {
        params: { id: id }
      })
      .then(response => {
        console.log(response.data)
        this.posts = this.posts.filter(post => post.id != id)
      })
      .catch(error => {
        this.posts = [{ entry: 'There was an error: ' + error.message }]
      })
    }
  }
}
</script>

<template>
  <!-- Loop through all posts and render each one using the blog-post component -->
  <blog-post
    v-for="post in posts"
    :key="post.id"
    :subject="post.subject"
    :entry="post.entry"
    :mood="post.mood"
  >
    <button @click="deletePost(post.id)">Delete</button>
  </blog-post>
</template>
