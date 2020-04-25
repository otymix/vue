<template>
    <div>

      <div class="typewriter">
        <h1 >Estimation du nombre d'infecté(e)s en France 🇫🇷 </h1>
      </div>

      <br />

 <v-card class="mx-auto" max-width="80%">
      <v-img class="white--text align-end"  height="200px"   src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/langfr-1280px-Flag_of_France.svg.png"  >
        <v-card-title style="background-color:#0000008c"> Chiffres clés estimées</v-card-title>
      </v-img>
  
      <v-card-subtitle class="pb-0">Aujourd'hui</v-card-subtitle>
  
      <v-card-text class="text">
           <br /> 
           <h2 class="font-weight-medium txtEffect" style="color:black ; line-height: 1.2em"> En se basant sur le taux de mortalité de <em class="oms">2%</em> du Covid-19, en partant du nombre total de décés actuel <p class="number">  {{covidDataFR.data.countrydata[0].total_deaths}}</p> , le nombre de cas des contaminés en France serait estimé alors à  <h2 class="number"> {{ estimatedCases }}</h2>
           Ainsi le pourcentage de la population immunisé à l'heure actuelle est : <p class="number">{{ this.estimatedPercentage }} %</p> 
           Aussi, selon les dernières statistiques du nb de morts/Jour, la France enregistre quasiment 
            <div class="number"> {{ this.oneDeathPerXmin }} morts par minute </div> ! 
          </h2>
      </v-card-text>
  
      <v-card-actions>
        <v-btn     color="cyan"     text >     
          Partager
        </v-btn>
  
        <v-btn     color="blue"      text >
          Puis-Je-Survivre-Au-Covid?
        </v-btn>
      </v-card-actions>
    </v-card>
     
    </div>
</template>


<script>

let covidApiEndpoint = 'https://api.thevirustracker.com/free-api?countryTotal=FR'

//let CountryCode = 'FR'
//const request = require('request')
import axios from 'axios';




var show = true


export default {
 
    methods:{

    
         getLast24HoursStats() {
        
                                      try {         
                   
                axios.get(covidApiEndpoint).then( 
                    response => { 
                        this.covidDataFR = response
                        //let _deathsPerDay_FR = 531
                        //this.oneDeathPerXmin =  1 * (24 / this.covidDataFR.data.countrydata[0].total_new_deaths_today )* 60
                        this.oneDeathPerXmin =  Math.round(1 * (24 / 544 )* 60)
                        
                        let total_deaths = response.data.countrydata[0].total_deaths
                        let fr_population = 67000000
                        this.estimatedCases = (total_deaths * 100 / 2)
                        this.estimatedPercentage = (this.estimatedCases/fr_population * 100).toFixed(2)
                        console.log(`estimatedCases : ${this.estimatedCases}`) 
                        
                    } 
            );
              }
  catch (error)
        {
                console.log(error);
        }


        }
        
    },
    data: ()=>{
        return {
            todaysDeaths:0,
            TotalDeaths:0,
            show,
            oneDeathPerXmin:'',
            estimatedPercentage: '',
            covidDataFR:[],
            estimatedCases:''
        }
    },
    created(){

          this.getLast24HoursStats()
              

        },
    
}
</script>


<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Baloo+Bhaina+2:wght@500&display=swap');

.number{
   //background-color:  #524fff;
    margin:10px;
    color: red;
   //border:5px solid black;
   //border-radius: 15px;
    display: inline;
   //padding:.35rem .5rem;
   //float:right
}

.txtEffect{
     font-family: 'Baloo Bhaina 2', cursive;
      line-height: 1.2rem;
}

.h1{
    color:black;
    line-height: 1.2rem;
   
   
    
}
.oms{
    color:red

}


/* DEMO-SPECIFIC STYLES */
.typewriter h1 {
  color: black;
  font-family: monospace;
  overflow: hidden; /* Ensures the content is not revealed until the animation */
  border-right: .15em solid orange; /* The typwriter cursor */
  white-space: nowrap; /* Keeps the content on a single line */
  margin: 0 auto; /* Gives that scrolling effect as the typing happens */
  letter-spacing: .15em; /* Adjust as needed */
  animation: 
    typing 3.5s steps(30, end),
    blink-caret .5s step-end infinite;
}

/* The typing effect */
@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

/* The typewriter cursor effect */
@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: orange }
}

</style>