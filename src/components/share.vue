<template>
    
  <div>
       <!--twitter>
    <div slot="loading">loading .....</div>
    <a class="twitter-timeline" href="https://twitter.com/realDonaldTrump?ref_src=twsrc%5Etfw">Tweets by realDonaldTrump</a>
  </twitter-->
         <link rel="stylesheet" 
        href="node_modules/@fortawesome/fontawesome-free/css/all.css">

      <div class="twitter" >
           <twitter> 
                <div slot="loading">loading .....</div>
                <a href="https://twitter.com/share?ref_src=twsrc%5Etfw" class="twitter-share-button" data-text="The estimated possibly undetected Covid-19 infections number in France 🇫🇷..." data-url="http:/thecoronavirus.site" data-via="otymix" data-hashtags="covid19" data-lang="fr" data-show-count="false">Tweet</a>        
            </twitter>

      </div>

      <div class="whatsapp" >
          <a style="color:#075e54; text-decoration:none" href="https://wa.me/?text=Check%20the%20%28real%29%20estimated%20Covid%20cases%20in%20France%20..%20http%3A%2F%2Fthecoronavirus.site">Partager <i style="color:#25d366" class="fab fa-whatsapp "></i> </a>
      </div>

  </div>

</template>

<script>
import twitter from 'vue-twitter'

import Vue from 'vue'


Vue.use(twitter)
export default {

    components: {
    
  },
      methods: {
    execute: function() {
             
            
    }
  },
 data: () => {
       return {
          author: "Oty"
       }
    
}
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Baloo+Bhaina+2:wght@500&display=swap');
.twitter{
margin: 10px;
display: inline-block;
padding: 5px;
}

.whatsapp{
margin: 10px;
display: inline-block;
padding: 5px;;
}
</style>