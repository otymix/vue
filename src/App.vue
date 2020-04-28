<template>

   <v-app>
      <v-content class="black" >
        <v-container >
                <FirstComponent/>
                <getDataCovid />
                <share />
        </v-container>
      </v-content>
      
    </v-app>
 
</template>

<script>

import FirstComponent from './components/FirstComponent';
import getDataCovid from '@/components/getDataCovid.vue';


export default {
  name: 'App',

  components: {

    FirstComponent,
    getDataCovid
  },

  data: () => ({
    //
  }),
};
</script>
