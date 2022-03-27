<template>
    <div class="container">
        <div v-for="post in posts" :key="post.slug" class="info_post">
            <img v-if="post.image" :src="`/storage/${post.image}`" :alt="post.title">
            <div class="title">{{post.title}}</div>

            <div v-if="post.category" class="category">{{post.category.name}}</div>
            <ul class="tags">
                <li v-for="tag in post.tags" :key="tag.slug" class="tag">{{tag.name}}</li>
            </ul>

            <p class="content">{{post.content}}</p>

            <router-link :to="{ name: 'single-post', params: {slug: post.slug} }">Visualizza Post</router-link>
        </div>
    </div>
</template>

<script>

export default{
    name: "Posts",
    data(){
        return {
            posts: [],
        };
    },
    created() {
        axios
        .get("/api/posts")
        .then((response)=>{
            this.posts = response.data
        })
    }
}

</script>

<style lang="scss" scoped>

.container{
    width: 100%;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;

    .info_post{
    width: 18%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    background-color: white;
    padding: 20px;
    margin-bottom: 20px;
    margin-right: 20px;

    img{
        width: 275px;
    }

    .title{
    font-size: 30px;
    font-weight: bold;
    padding: 5px;
    }

    .category{
        background-color: deepskyblue;
        text-transform: uppercase;
        font-size: 13px;
        height: 23px;
        width: 30%;
    }

    .tags{
        background-color: grey;
        width: 15%;
        height: 23px;
    }

    .tag ul li{
        color: black;
    }

    .content{
        font-size: 15px;
    }
}
}


</style>