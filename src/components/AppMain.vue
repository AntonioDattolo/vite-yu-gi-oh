<script>

import cards from '../store/Card.js';
import AppMainCard from './AppMainCard.vue';
export default {
    
  components: {
   AppMainCard
  },
  data() {
    return {
        cards,

    }
  },
  // methods: {
  //   ///
  // },
  // mounted: {

  // }
}


</script>

<template>
  <header>
    <AppHeader />
  </header>
  <main class="container">

    <section class="d-flex justify-content-between flex-wrap p-3">
      <AppMainCard v-for="card in cards" :cards="card"/>
      
    </section>
  </main>
</template>

<style scoped>

</style>
