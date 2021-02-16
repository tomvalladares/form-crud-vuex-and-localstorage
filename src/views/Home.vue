<template>
  <div class="home mt-5">
    <form @submit.prevent="procesarInput">
    <Input :tarea="tarea"/>
    </form>
    <hr>
    <ListaTareas/>
  </div>
</template>

<script>
import ListaTareas from '../components/ListaTareas'
import Input from '../components/Input';
import {mapActions } from 'vuex';
const shortid = require('shortid')


export default {
  name: 'Home',
  components: {
   Input, ListaTareas
  },
  data() {
      return {
          tarea: {
              id: '',
              nombre: '',
              categorias: [],
              urgencia: '',
              numero: 0
          }
      }
  },
  methods: {
    ...mapActions(['setTareas']),
    procesarInput() { 
        console.log(this.tarea)
        if(this.tarea.nombre.trim() === '') {
            console.log('CampoVacio');
            return
        } 
        console.log('no está vacío');
        //   generar id 
        this.tarea.id = shortid.generate()
        // enviar datos a vuex
        this.setTareas(this.tarea)

          this.tarea= {
              id: '',
              nombre: '',
              categorias: [],
              urgencia: '',
              numero: 0
          }
    },
  
}
}
</script>
