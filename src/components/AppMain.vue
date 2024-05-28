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
    getValue(){
      myData.apiCards =[]
      console.log(myData.archetype)
      axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=` + myData.archetype).then((result) => {
          let card = result.data;
          myData.apiCards.push(card.data)
          console.log(myData.apiCards[0], "apiCards")
        });
    }
    

  },
  mounted() {
    // axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=85&race=dragon`).then((result) => {
    //       let card = result.data;
    //       myData.apiCards.push(card.data)
    //       console.log(myData.apiCards[0], "apiCards")
    //     });
    
        
   }
}


</script>

<template>
  <main class="container myBg">
    <section class="d-flex justify-content-between flex-wrap p-3">
      <!-- <AppMainCard v-for="card in myData.cards" :cards="card"/> -->
       <h1 class="col-12">BONUS DA 20 CARTE A PARTIRE DALLA 15ESIMA CON CHIAMATA AXIOS</h1>
       <button @click="getValue">clicca</button>

         <!-- <pre v-for="element in myData.apiCards">{{ element }}</pre>  -->
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
