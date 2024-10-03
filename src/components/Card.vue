<template>
  <div class="card" style="width: 18rem;">
    <img :src="game.background_image" class="card-img-top" alt="Card image cap">
    <h5 class="card-title bold-text">{{game.name}}</h5>
    <div class="card-body">
      <p class="card-text">Rating:  {{game.rating}}</p>
      <p class="card-text">Released:  {{game.released}}</p>
      <p class="card-text">Update:  {{game.updated}}</p>
      <a @click= "redirect(game.name)" class="btn btn-primary"> Opinar {{buttonText}}</a> &nbsp; &nbsp;
      <i @click="emulateError" class= "fa-brands fa-gratipay fa-xl" style="color: #e72a08;"></i>
    </div>
  </div>
</template>

<script>
export default {
  name:"Card-components" ,
  props: {
      game:{
      type:Object ,
      Required:true
    }
  },
  methods:{
    redirect (nombreJuego){
   this.$router.push("/opiniones/"+nombreJuego)
  },
  emulateError() {
      this.$router.push('/NotFound')
    }
  }}
</script>

<style scoped>
.bold-text {
  font-weight: bold;
}
</style>
