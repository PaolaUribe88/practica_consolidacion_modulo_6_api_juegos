<template>
    <div id="JuegosComponents">
       <div class="container">
        <h1 id="tituloJuegos">Listado de Juegos disponibles</h1>
       </div>
        <div class="contenedorJuegos">
            <div v-for="(juego, index) in juegos" :key="index" class="card m-2" style="width: 20%;">
                <img v-bind:src="juego.background_image" class="card-img-top" alt="logo">
                    <div class="card-body">
                        <h5 class="card-title">Nombre: {{ juego.name }} </h5>
                        <p>ESRB Rating: {{ juego.esrb_rating.name }}</p>
                    </div>
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">Rating: {{ juego.rating }}</li>
                            <li class="list-group-item">Released: {{ juego.released }} </li>
                            <li class="list-group-item">Updated: {{ juego.updated }}</li>
                        </ul>
                        <div class="card-body">
                            <a v-on:click="mostrarOpiniones(juego.name)" class="btn btn-primary m-2">Opinar</a>
                            <a v-on:click="irAdministracion(juego.name)" class="btn btnRed"><i class="fa-solid fa-heart-circle-plus" ></i></a>
                        </div>
            </div>
        </div>      
    </div>
</template>
<script>
import axios from 'axios';
export default{
    name:'JuegosComponents',
    data: function(){
        return{
            cantidadJuegos:0,
            juegos:[],
        }
    },
    methods:{
        consumirApiJuegos: function(){
            //funcion dinamica
        let url = `https://api.rawg.io/api/games?key=ef9df7bfa7b147bc8579b4e5fe7f19ad`;
        axios(url)
            .then(respuesta =>{
            // console.log(respuesta);
            // console.log(respuesta.data.results[9].name)
            this.cantidadJuegos= respuesta.data.results.length; 
            for(let i=0; i<this.cantidadJuegos; i++){
                this.juegos.push(respuesta.data.results[i]);
                
            }
            
                
            })
            .catch(error =>{
                console.log(error);
            });
    },
        mostrarOpiniones: function(nombreJuegos){
            this.$router.push(`/opiniones/${nombreJuegos}`)
        },
        irAdministracion:function(nombreJuegos){
            this.$router.push(`/administracion/${nombreJuegos}`);
        }
        
    },
    created(){
        this.consumirApiJuegos();
    }
}
</script>
<style scoped>
#tituloJuegos{
    text-align: start;
    color: black;
}
#JuegosComponents{
    background-color: blueviolet;
}
.contenedorJuegos{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    
}
.btnRed{
    color: red;
}
</style>