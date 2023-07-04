<template>
    <div id="NotFound">
        <h1>Pagina no Encontrada</h1>
        <p></p>
        <router-Link to="/">Volver a Home</router-Link>
    </div>
</template>
<script>
export default{
    name:'NotFound',
    data: function(){
        return{

        }
    },
    methods:{

    }
}
</script>
<style scoped>
#NotFound{
    background-image: url(../assets/logo404.png);
}

</style>