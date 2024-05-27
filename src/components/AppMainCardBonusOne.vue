<script>

export default {
   name: "AppMainCard",
   props :
        ["cardss"]

   ,
   
  
  data() {
    return {
        

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
  
    
    <div class="card myWidth text-white">
      <img :src="cardss.card_images[0].image_url" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title"> {{ cardss.name }}</h5>
        <p class="card-text">{{ cardss.type }}</p>
        
      </div>
    </div>
  
  <!-- <pre>
    {{ cardss.card_images[0].image_url}}

</pre>   -->
</template>

<style scoped>
.myWidth{
    width: calc((100% / 5) - 1.5rem);
    background-color: transparent;
    border: none;
}
</style>