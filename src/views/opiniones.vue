<template>
  <div>
    <h1> {{name}}</h1>
    <form @submit.prevent="guardarOpinion">
      <div class="form-group">
        <label for="">nombre</label>
        <input v-model="nuevoAutor" placeholder="Tu nombre" />
      </div>
      <div class="form-group">
        <label for="">opinion</label>
       <textarea v-model="nuevaOpinion" placeholder="Escribe tu opinión"></textarea>
      </div>
      <br>
    <div>
      <button type="submit" class="btn btn-info">{{ editando ? 'Actualizar' : 'Agregar' }} Opinión</button>
    </div>

    </form>
    <div v-if="opiniones.length > 0">
      <div v-for="opinion in opiniones" :key="opinion.id">
        <p>{{ opinion.autor }}: {{ opinion.texto }}</p>
        <button @click="editarOpinion (opinion)" type="button" class="btn btn-warning">Editar</button>
        <button @click="eliminarOpinion(opinion.id)" type="button" class="btn btn-danger">Eliminar</button>
      </div>
    </div>
    <p v-else>No existen opiniones para este juego.</p>

    
  </div>
</template>

<script>
export default {
  name:"opinion-vue",
  data() {
    return {
      opiniones: [],
      nuevoAutor: '',
      nuevaOpinion: '',
      editando: false,
      opinionEditando: null
    };
  },
  methods: {
    guardarOpinion() {
      if (this.editando) {
        this.opinionEditando.autor = this.nuevoAutor;
        this.opinionEditando.texto = this.nuevaOpinion;
        this.editando = false;
        this.opinionEditando = null;
      } else {
        const nuevaOpinion = {
          id: Date.now(),
          autor: this.nuevoAutor,
          texto: this.nuevaOpinion
        };
        this.opiniones.push(nuevaOpinion);
      }
      this.nuevoAutor = '';
      this.nuevaOpinion = '';
    },
    editarOpinion(opinion) {
      this.nuevoAutor = opinion.autor;
      this.nuevaOpinion = opinion.texto;
      this.editando = true;
      this.opinionEditando = opinion;
    },
    eliminarOpinion(id) {
      this.opiniones = this.opiniones.filter(opinion => opinion.id !== id);
    }
  },
  props:{
    name:{
      type:String,
      Required:true,
    }
  },
  
};
</script>

<style scoped>

.form-group{
  display:flex;
  flex-direction: column;
  width: 50%;
  margin: 0 auto;
}
</style>.