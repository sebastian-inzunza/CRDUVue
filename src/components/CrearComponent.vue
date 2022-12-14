<template>
    <div class="container">
      <div class="card">
        <div class="card-header">
          Agregar nuevo empleados
        </div>
        <div class="card-body">
          <form v-on:submit.prevent = "agregarRegistro">
            <div class="form-group">
              <label for="Nombre">Nombre</label>
              <input type="text"
                class="form-control" required v-model="empleado.nombre" name="nombre" id="nombre" aria-describedby="helpId" placeholder="">
              <small id="helpId" class="form-text text-muted">Escribe el nombre del empleado</small>
            </div>
            <div class="form-group">
              <label for="">Correo</label>
              <input type="email" required v-model="empleado.correo" class="form-control" name="correo" id="correo" aria-describedby="emailHelpId" placeholder="">
              <small id="emailHelpId" class="form-text text-muted">Escribe el coreo electronico</small>
            </div>
            
            <div class="btn-group" role="group" aria-label="">
              <button type="submit" class="btn btn-success">Agregar</button>
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
    methods:{
      agregarRegistro(){
        console.log(this.empleado);
        var datosEnviar={nombre:this.empleado.nombre, correo:this.empleado.correo};
        fetch('http://localhost/api/?insertar=1' ,{
          method: 'POST',
          body:JSON.stringify(datosEnviar)
        })
        .then(respuesta=>respuesta.json())
        .then((datosRespuesta=>{
          console.log(datosRespuesta)
          window.location.href='listar'
        }))
      }
    }

  }
  </script>
  