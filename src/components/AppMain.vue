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
    // getValue(){
    //   myData.apiCards =[]
    //   console.log(myData.archetype)
    //    axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=` + myData.archetype).then((result) => {
    //       let card = result.data;
    //       myData.apiCards.push(card.data)
    //       console.log(myData.apiCards[0], "apiCards")
    //     });
    // }
    

  },
  mounted() {
    axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=85&race=dragon`).then((result) => {
      myData.apiCards = result.data.data;
      // myData.apiCards.push(card.data)
      console.log(myData.apiCards, "apiCards")
    });
  }
}


</script>

<template>
  <main class="container myBg">
    <!-- <button @click="getValue">Scegli il tuo set</button>  -->
    <section class="d-flex flex-wrap p-3">
      <!-- <AppMainCard v-for="card in myData.cards" :cards="card"/> -->
      
       <h1 class="col-12">ho trovato {{ myData.apiCards.length }} carte</h1>
       

         <!-- <pre v-for="element in myData.apiCards">{{ element }}</pre>  -->
         <AppMainCardBonusOne v-for="card in myData.apiCards" :cardss="card"/>
         
      
    </section>
  </main>
</template>

<style scoped>
.myBg{
  background-color: rgb(105, 105, 104);
  border-radius: 35px;
}
</style>
