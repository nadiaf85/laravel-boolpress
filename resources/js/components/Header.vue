<template>
    <div>
        <header>
            <nav>
                <li><router-link class="link" :to="{ name: 'home' }">HOME</router-link></li>
                <li><router-link class="link" :to="{ name: 'about' }">CHI SIAMO</router-link></li>
            </nav>
            
        </header>
    </div>
    
</template>

<script>

export default{
    name: "Header",
}
</script>

<style lang="scss" scoped>

nav{
    width: 100%;
    height: 100%;
    margin: auto;
    display: flex;
    background-color: lightskyblue;

    li{
        list-style: none;
        height: 100%;
        line-height: 90px;
        margin: 0 10px;
    }

    .link{
        text-decoration: none;
        text-transform: uppercase;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        color: #191970;
        padding: 25px;
    }
}

</style>