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
                class="form-control" v-model="empleado.nombre" name="nombre" id="nombre" aria-describedby="helpId" placeholder="">
              <small id="helpId" class="form-text text-muted">Escribe el nombre del empleado</small>
            </div>
            <div class="form-group">
              <label for="">Correo</label>
              <input type="email" v-model="empleado.correo" class="form-control" name="correo" id="correo" aria-describedby="emailHelpId" placeholder="">
              <small id="emailHelpId" class="form-text text-muted">Escribe el coreo electronico</small>
            </div>
            
            <div class="btn-group" role="group" aria-label="">
              <button type="submit" class="btn btn-success">Agregar</button>
              <button type="button" class="btn btn-warning">Cancelar</button>
           
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
        var datosEnviar=(nombre:this.empleado.nombre, Correo:this.empleado.correo)
      }
    }

  }
  </script>
  