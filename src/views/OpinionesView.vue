<template>
    <div id="OpinionesView">
     
        <h1>Componente OpinionesView</h1>
        <p>Escribe tu opinión para el juego: {{ nombre }}</p>
        <hr>
        <div class="container" id="formulario">
            <form >
                <div class="mb-3">
                    <label for="txtNombre" class="form-label">Nombre:</label>
                    <input type="text" class="form-control" id="txtNombre" v-model="nombreEnviado" aria-describedby="txtNombreHelp">
                    <div id="txtNombreHelp" class="form-text">Ingrese su nombre para la opinión.</div>
                </div>
                <div class="mb-3">
                    <label for="txtOpinion" class="form-label">Opinión:</label>
                    <input type="text" class="form-control" id="txtOpinion" v-model="opinionEnviada">
                </div>

                <button type="submit" v-on:click.prevent="agregarOpinion()" class="btn btn-info">{{nombreBoton}}</button>
            </form>
        </div>
        
        <h2>A continuación podrás ver tu opinión</h2>
        <div class="container" id="sinOpiniones" v-if="cantidadOpiniones<1">
            <p>No existen opiniones para mostrar</p>
        </div>
        
        <div class="container">
            <div class="accordion" id="accordionExample" v-if="cantidadOpiniones>0">
                <div class="accordion-item" v-for="(elemento,index) in opiniones">
                    <h2 class="accordion-header">
                    <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                        Opinion creada por: {{ elemento.nombre }}
                    </button>
                    </h2>
                    <div id="collapseOne" class="accordion-collapse collapse show" data-bs-parent="#accordionExample">
                        <div class="accordion-body">
                            {{ elemento.opinion }}
                        </div>
                        <button class="btn btn-danger m-2" v-on:click="eliminarOpinion(index)">Eliminar</button>
                        <button class="btn btn-warning m-2" v-on:click="editarOpinion(index)">Editar</button>
                    </div>
                </div>
            </div>
        </div>

        <router-link to="/">Volver</router-link>
    </div>
</template>

<script>
export default{
    name:'OpinionesView',
    props:['nombre'],
    data: function(){
        return{
            cantidadOpiniones: 0,
            nombreEnviado:'',
            opinionEnviada:'',
            opiniones:[],
            nombreBoton:'Agregar',
            indiceActualizar:0,


        }
    },
    methods:{
        agregarOpinion: function(){

            if(this.nombreBoton == 'Agregar'){
                this.cantidadOpiniones++;
                let nuevaOpinion={
                nombre:this.nombreEnviado,
                opinion:this.opinionEnviada,
                                };
                this.opiniones.push(nuevaOpinion);
                this.nombreEnviado='';
                this.opinionEnviada='';
            }
            else if(this.nombreBoton=='Actualizar'){
                let opinionActualizada={
                    nombre:this.nombreEnviado,
                    opinion:this.opinionEnviada,
                                };
                this.opiniones.splice(this.indiceActualizar,1, opinionActualizada);
                alert('La opinión fue actualizada. Revise el acordeon con la nueva inforación');
            }

        },
        eliminarOpinion:function(indice){
            this.cantidadOpiniones--;
            this.opiniones.splice(indice,1);
        },
        editarOpinion:function(indice){
            this.nombreEnviado=this.opiniones[indice].nombre;
            this.opinionEnviada=this.opiniones[indice].opinion;
            this.nombreBoton = 'Actualizar';
            this.indiceActualizar = indice;
            alert('Va a editar una opinión. Revise el formulario con la información cargada');
        },
    }

}
</script>
<style scoped>
nav{
    text-align: start;
    background-color: black;
    color: white;
}
#formulario{
    text-align: start;
    border: solid 2px rgb(200, 198, 198);
    padding-top: 10px;
    padding-bottom: 20px;
}
#sinOpiniones{
    text-align: start;
    border: solid 2px red;
    background-color: lightpink;
    color: rgb(133, 32, 32);
}
</style>