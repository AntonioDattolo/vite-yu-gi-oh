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
      myData

    }
  },
  methods: {
    
  },
  created(){
   

  },
  mounted() {
    axios.get(`https://db.ygoprodeck.com/api/v7/archetypes.php`).then((result) => {
          myData.archetypeList= result.data;
          console.log(myData.archetypeList)
        });    
  }
}
</script>

<template>
  <AppHeader /> 
  <section class="container">
    <select name="Archetype"id="" class="w-25" v-model="myData.archetype"> 
      <option v-for="element of myData.archetypeList">{{ element.archetype_name }}</option>
    </select> 
  </section>
  <AppMain />
  <AppFooter />
</template>

<style scoped>
  
</style>