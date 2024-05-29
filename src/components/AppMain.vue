<script>

import myData from '../store/Card.js';
import AppMainCard from './AppMainCard.vue';
import AppMainCardBonusOne from './AppMainCardBonusOne.vue'
export default {
    
  components: {
   AppMainCard,
   AppMainCardBonusOne
  },
  data() {
    return {
        myData,

    }
  },
  methods: {
    
  },
  mounted() {
    // axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=85&race=dragon`).then((result) => {
    //   myData.apiCards = result.data.data;
    //   console.log(myData.apiCards, "apiCards")
    // });
  }
}


</script>

<template>
  <main class="container myBg">
    <section class="d-flex flex-wrap p-3">
      <h1 class="col-12">ho trovato {{ myData.apiCards.length }} carte</h1>
      <AppMainCardBonusOne v-for="card in myData.apiCards" :cardss="card" />
    </section>
  </main>
</template>

<style scoped>
.myBg{
  background-color: rgb(105, 105, 104);
  border-radius: 35px;
}
</style>
