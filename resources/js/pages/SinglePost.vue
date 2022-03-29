<template>
    <div class="container">
        <div class="info_post">
            <h1 class="title">{{post.title}}</h1>
            <div v-html="post.content" class="content"></div>
            <div v-if="post.category" class="category"><strong>Categoria: </strong>{{post.category.title}}</div>
            <ul class="tags">
                <li v-for="tag in post.tags" :key="tag.slug" class="tag">#{{tag.title}}</li>
            </ul>
            <img v-if="post.image" :src="`/storage/${post.image}`" :alt="post.title">
            <li><router-link class="back" :to="{ name: 'home'}">Indietro</router-link></li>
        </div>
    </div>
</template>

<script>

export default{
    name: "SinglePost",
    data(){
        return {
            post: {},
        };
    },
    created() {
        axios
        .get(`/api/posts/${this.$route.params.slug}`)
        .then((response)=>{
            this.post = response.data
        }).catch ( (error) =>{
            // handle error
            this.$router.push({name: 'page-404'});
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
        width: 80%;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        padding: 20px;
        margin-bottom: 20px;
        margin-right: 20px;

    img{
        width: 80%;
        margin-bottom: 20px;
    }

    .title{
        font-size: 30px;
        font-weight: bold;
        padding: 5px;
    }

    .category{
        background-color: lightskyblue;
        text-transform: uppercase;
    }

    .tags{
        list-style: none;
        margin: 10px 0;
        padding: 0;
        display: flex;

        .tag{
            background-color: #008b8b;
            color: white;
            padding: 5px;
            margin: 0 5px;
            border-radius: 5px;
            font-size: 12px;
        }
    }

    li{
        list-style: none;
        text-transform: uppercase;
    }

    .back{
        text-transform: uppercase;
    }

    .content{
        font-size: 15px;
    }
}
}
</style>