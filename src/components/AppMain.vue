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
    axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=5&offset=15`).then((result) => {
          let card = result.data;
          myData.apiCards.push(card.data)
          console.log(myData.apiCards[0], "apiCards")
        });
   }
}


</script>

<template>
  <main class="container myBg">
    <section class="d-flex justify-content-between flex-wrap p-3">
      <AppMainCard v-for="card in myData.cards" :cards="card"/>
       <h1 class="col-12">BONUS DA 5 CARTE CON CHIAMATA AXIOS</h1>

         <!-- <pre v-for="element in myData.apiCards">{{ element }}</pre> -->
         <AppMainCardBonusOne v-for="card in myData.apiCards[0]" :cardss="card"/>
         
      
    </section>
  </main>
</template>

<style scoped>
.myBg{
  background-color: rgb(105, 105, 104);
  border-radius: 35px;
}
</style>
