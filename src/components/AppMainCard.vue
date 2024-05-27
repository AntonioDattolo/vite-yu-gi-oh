<script>

export default {
   name: "AppMainCard",
   props :
        ["cards"]

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
    <div class="card myWidth">
        <img :src="cards.card_images[0].image_url" class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title"> {{ cards.name }}</h5>
            <p class="card-text">{{ cards.type }}</p>

        </div>
    </div>
    <!-- <pre>
    {{ cards.type }}

</pre> -->
</template>

<style scoped>
.myWidth{
    width: calc((100% / 5) - 1.5rem);
}

</style>
