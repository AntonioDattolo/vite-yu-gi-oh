<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import AppFooter from './components/AppFooter.vue'
import myData from './store/Card.js';

export default {
  components: {
    AppHeader,
    AppMain,
    AppFooter
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
          myData.apiCards= result.data.data;
          console.log(myData.apiCards, "apiCards")
        });
    }
    
  },
  created(){
    axios.get(`https://db.ygoprodeck.com/api/v7/archetypes.php`).then((result) => {
      myData.archetypeList = result.data;
      console.log(myData.archetypeList)
      myData.archetype = myData.archetypeList[0]
      console.log(myData.archetype.archetype_name)
    });
   

  },
  mounted() { 
          
  }
}
</script>

<template>
  <AppHeader /> 
  <section class="container">
    <select @change="getValue()" name="Archetype" id="" class="w-25" v-model="myData.archetype"> 
      <option v-for="element in myData.archetypeList">{{ element.archetype_name }}</option>
    </select> 
  </section>
  <AppMain />
  <AppFooter />
</template>

<style scoped>
  
</style>