<template>
 
    <div>
        <h1>Home Page</h1>
        <Posts/>
    </div>
    
</template>

<script>
import Posts from '../components/Posts.vue'

export default{
    name: "Home",
    components:{
        Posts
    }
}

</script>

<style lang="scss" scoped>

h1{
    text-align: center;
    text-transform: uppercase;
    margin-bottom: 60px;
    color: #191970;
}

</style>