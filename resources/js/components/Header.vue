<template>
    <div>
        <header>
            <nav>
                <li><router-link :to="{ name: 'home' }">HOME</router-link></li>
                <li><router-link :to="{ name: 'about' }">CHI SIAMO</router-link></li>
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

</style>