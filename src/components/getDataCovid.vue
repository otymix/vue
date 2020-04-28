<template>
    <div>

      <div class="typewriter">
        <h1 >Esimation du nombre d'infecté(e)s en France 🇫🇷 </h1>
      </div>

      <br />

 <v-card  class="mx-auto" max-width="80%">
      <v-img class="white--text align-end"  height="200px"   src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/langfr-1280px-Flag_of_France.svg.png"  >
        <v-card-title style="background-color:#0000008c"> En attendant un dépistage massif... </v-card-title>
      </v-img>
  
      <v-card-subtitle class="pb-0">*ceci est une estimation basée sur les 2 élements les plus fiables (nb décés, taux de mortalité)</v-card-subtitle>
  
      <v-card-text class="text">
           <br /> 
           <h2 class="font-weight-medium txtEffect" style="color:black ; line-height: 2.5rem"> En se basant sur le taux de mortalité du Covid-19 <em style="color:#796262">(approx.)</em> de <strong class="oms">2%</strong>, sachant que le nb total de décés actuel :<p class="number">{{covidDataFR.data.countrydata[0].total_deaths}}</p>, le nombre de contaminé(e)s en France serait estimé alors à  <h1 class="estimated"> {{estimatedCases_formatted}}</h1>
           résultant en un pourcentage de la population immunisé à l'heure actuelle de :<h1 class="number">{{ this.estimatedPercentage }} %</h1> 
           <!--
           Aussi, selon les dernières statistiques du nb de morts/Jour, la France enregistre quasiment 
            <div class="number"> {{ this.oneDeathPerXmin }} morts par minute </div> 
            -->
          </h2>
      </v-card-text>
  
      <v-card-actions>
        <!--v-btn     color="cyan"     text >     
          Partager
        </v-btn-->
        <share />
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
import share from '@/components/share.vue';



var show = true


export default {
  components : {
    share
  },

 
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
                        let part1 = this.estimatedCases.toString().substr(0,1)
                        let part2 = this.estimatedCases.toString().substr(1, 3)
                        let part3 = this.estimatedCases.toString().substr(4, 6)
                        this.estimatedCases_formatted = part1.concat(" "+part2).concat(" "+part3)
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
            estimatedCases:'',
            estimatedCases_formatted:''
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
  
    margin:10px;
    display: inline;
    color:#111873 !important;
}

.estimated{
    display: inline;
    display: inline;
    color: black;
    background-image: linear-gradient(to left, #ed2436, #e6071b42, #ffffff, #515e9a8c, #021d97);
    background-repeat: no-repeat;
    background-size: 100% 0.2em;
    background-position: 0 89%;
    border-radius: 5px;
    transition: background-size 0.25s ease-in;
    line-height:2;
}

.txtEffect{
     font-family: 'Baloo Bhaina 2', cursive;
      line-height: 1.2rem;
}

.h1{
    color:black;
    line-height: 2.4rem;
   
   
    
}
.oms{
    color:red;
}


/* DEMO-SPECIFIC STYLES */
.typewriter h1 {
  color: white;
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
  50% { border-color: red }
}

</style>