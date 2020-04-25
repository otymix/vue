<template>
  <div class="home">
    <img alt="Stay Home" src="https://ressources.blogdumoderateur.com/2020/03/stay-home-instagram-.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <FirstComponent />
    <getDataCovid />
  </div>
</template>

<script>
// @ is an alias to /src

import FirstComponent from '@/components/FirstComponent.vue'
import getDataCovid from '@/components/getDataCovid.vue'

export default {
  name: 'Home',
  components: {

    FirstComponent,
    getDataCovid
  }
}
</script>
