<template>
  <div class="not-found">
    <h1>Error 404</h1>
    <p>Página no encontrada</p>
    <router-link to="/">Volver al inicio</router-link>
  </div>
</template>

<script>
export default {
  name: 'NotFound',
  mounted() {
    setTimeout(() => {
      this.$router.push('/')
    }, 3000)
  }
}
</script>

<style scoped>
.not-found {
  text-align: center;
  margin-top: 50px;
}

.not-found h1 {
  font-size: 3em;
  color: red;
}

.not-found p {
  font-size: 1.5em;
}

.not-found a {
  text-decoration: none;
  color: blue;
}
</style>
