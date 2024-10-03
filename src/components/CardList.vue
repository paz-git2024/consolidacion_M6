<template>
  <div class="container">
    <div class="row">
      <div class="col-md-3" v-for="(game, index) in games" :key="index">
        <Card
          :game="game"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  components: {
    Card
  },
  props:{
    games:{
      type:Array,
      Required:true
    }
  },
  data() {
    return {

    }
  }
}
</script>
