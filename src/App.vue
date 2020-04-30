<template>

   <v-app>
      <v-content class="black" >
        <v-container >
                <Thehead />
                <getDataCovid />
                <share />
        </v-container>
      </v-content>
      
    </v-app>
 
</template>

<script>

import Thehead from './components/Thehead';
import getDataCovid from '@/components/getDataCovid.vue';


export default {
  name: 'App',

  components: {
    // eslint-disable-next-line vue/no-unused-components
    Thehead,
    getDataCovid
  },

  data: () => ({
    //
  }),
};
</script>
