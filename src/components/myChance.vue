<template>
    <div>
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
</style>