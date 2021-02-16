<template>
  <input 
          type="text" 
          class="form-control" 
          placeholder="Ingrese nombre"
          v-model.trim="tarea.nombre" 
          >
          <div class="form-check form-check-inline">
              <input class="form-check-input" type="checkbox" name="categoria" id="check1" v-model="tarea.categorias" value="javascript">
              <label class="form-check-label" for="check1"> Javascript</label>
          </div>
          <div class="form-check form-check-inline">
              <input class="form-check-input" type="checkbox" name="categoria" id="check2" v-model="tarea.categorias" value="nodejs">
              <label class="form-check-label" for="check2"> NodeJs</label>
          </div>
          <div class="mt-4">
            <div class="form-check form-check-inline">
                    <input name="urgencia" type="radio" id="radio-1" class="form-check-input" v-model="tarea.urgencia" value="urgente">
                    <label for="radio-1" class="form-check-label">Urgente</label>
            </div>
            <div class="form-check form-check-inline">
                    <input name="urgencia" type="radio" id="radio-2" class="form-check-input" v-model="tarea.urgencia" value="normal">
                    <label for="radio-2" class="form-check-label">Normal</label>
            </div>
          </div>
          <div class="mt-2">
              <input  class="form-control" type="number" v-model.number="tarea.numero">
              <!-- // aca el .number cambia a numero el valor ingresado en el input  -->
          </div>
          <button class="btn btn-dark mt-4 w-100" :disabled="desabilitado" type="submit">Procesar</button>
      
</template>

<script>
export default {
  props: {
    tarea: {
      type: Object
    },
  },
  computed: {
        desabilitado() { 
            return this.tarea.nombre.trim() == '' ? true : false
        }
  }
}
</script>

<style>

</style>