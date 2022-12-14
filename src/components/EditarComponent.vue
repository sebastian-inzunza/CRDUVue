<template>
    <div class="container">
      <div class="card">
        <div class="card-header">
          Editar nuevo empleados
        </div>
        <div class="card-body">
          <form v-on:submit.prevent = "actualizarRegistro">
            <div class="form-group">
              <label for="Nombre">Nombre</label>
              <input type="text"
                class="form-control" required v-model="empleado.nombre" name="nombre"  aria-describedby="helpId" placeholder="">
              <small id="helpId" class="form-text text-muted">Escribe el nombre del empleado</small>
            </div>
            <div class="form-group">
              <label for="">Correo</label>
              <input type="email" required v-model="empleado.correo" class="form-control" name="correo" id="correo" aria-describedby="emailHelpId" placeholder="">
              <small id="emailHelpId" class="form-text text-muted">Escribe el coreo electronico</small>
            </div>
            
            <div class="btn-group" role="group" aria-label="">
              <button type="submit" class="btn btn-success">Modificar</button>
              <router-link  :to="{name:'listar'}" class="btn btn-warning ">Cancelar</router-link>
            </div>

          </form>
        </div>
       
      </div>
        
    </div>
  </template>
  
  <script>
  export default {
    data(){
      return{
        
        empleado: {}
        
      } 
    },
    created: function(){
      this.obtenerInformacionID()
    },
    methods:{
      
      obtenerInformacionID (){
        fetch('http://localhost/api/?consultar='+ this.$route.params.id)
        .then(respuesta=>respuesta.json())
        .then((datosRespuesta)=>{
          console.log(datosRespuesta);
          this.empleado=datosRespuesta[0];

          
        })
        .catch(console.log)

        
      },
      actualizarRegistro(){
        var datosEnviar={id:this.empleado.id,nombre:this.empleado.nombre, correo:this.empleado.correo};
        fetch('http://localhost/api/?actualizar=' + this.$route.params.id,{
          method: 'POST',
          body:JSON.stringify(datosEnviar)
        })
        .then(respuesta=>respuesta.json())
        .then((datosRespuesta=>{
          console.log(datosRespuesta)
          window.location.href='../listar'
        }))
      }   
    }
  } //End of script
  </script>