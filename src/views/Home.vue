<template>

  <div class="home">
           <div>
             <div class="d-flex align-center justify-center">
                  <v-img 
                  class=" img-center shrink "
                  alt="Stay Home" 
                  src="https://ressources.blogdumoderateur.com/2020/03/stay-home-instagram-664x348.png" 
                  />
            </div>
    </div>
    <img alt="Stay Home" src="https://ressources.blogdumoderateur.com/2020/03/stay-home-instagram-.png" />

    <getDataCovid />
  </div>
</template>

<script>
// @ is an alias to /src

//import head from '@/components/head.vue'
import getDataCovid from '@/components/getDataCovid.vue'
import Thehead from '@/components/Thehead.vue'

export default {
  name: 'Home',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    Thehead,
    getDataCovid
  }
}
</script>
