<script>
    export default{
        data(){
            products: [
                {}
            ]
        }, 
        components{
            Product
        }


    }
</script> 

<template> 
    <Product v-for="product in products" :prod="product"></Product> 

</template>