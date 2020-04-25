<template>
    <div>
             <div class="d-flex align-center justify-center">
                  <v-img 
                  class=" img-center shrink "
                  alt="Stay Home" 
                  src="https://ressources.blogdumoderateur.com/2020/03/stay-home-instagram-664x348.png" 
                  />
            </div>
        <!--h1>First composant de 
               <span>{{author}}</span>
               &nbsp; <small>{{date}}</small>
               <span v-if="estVisible"  > Visible Attribute {{count}} </span>
         </h1>
         <v-btn @click="execute"  dark class="text-white deep-purple accent-4"> test </v-btn>
         <v-rating />
         <a :href=url > product link</a-->
    </div>
</template>

<script>


let today = new Date()
export default {
 //here your code JS   
  methods: {
    execute: function() {
             this.count+=1
            
    }
  },
 data: () => {
       return {
          author: "Oty",
          date: today,
          count:0,
          estVisible : true,
          url: "http://producthunt.com"
       }
    }
}
</script>

<style scoped>
h1{
    color:blue
}
span{
    color:black
}

small{
    color:darkorange
}
</style>