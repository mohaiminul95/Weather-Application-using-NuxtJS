<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col md="12">
          <v-card
            elevation="2"
            color="blue-grey darken-2 dark"
            >
            <v-card-text>
                <v-layout v-if="weather.weather">
                    <v-flex class="text-xs-center">
                        <center>
                            <h3>Temperature</h3>
                            <h2>{{ weather.name }}</h2>
                            <img :src="icon">
                            <h1>{{ temp() }}&deg;C</h1>
                            <p>{{ weather.weather[0].description }}</p>
                        </center>
                    </v-flex>
                </v-layout>    
            </v-card-text>  
        </v-card>
        <br>
        <v-form @submit.prevent="getWeatherInfo">
            <v-text-field
                label="Enter City Name..."
                solo
                v-model="city"
            >
            </v-text-field>
        </v-form>
        </v-col>
    </v-row>
  </v-container>
</template>

<script>

export default {
  data() {
      return {
          city: '',
          weather: {}
      }
  },
  computed: {
      icon() {
          return this.weather.weather ? `https://openweathermap.org/img/w/${this.weather.weather[0].icon}.png` : ''
      }
  },
  created() {
       this.getWeatherInfo()
  },  
  methods: {
      getWeatherInfo() {
        this.$axios.$get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=7aa5c71da109ded24da8c78d67f010ea`)
        .then(res=> (this.weather= res))
      },
      temp() {
          return Math.round(this.weather.main.temp - 273)
      }
  }
}
</script>

<style scoped>
    .v-card__title{
      color: #fff;
  }
  h1, h2, h3, p {
      color: #fff;
      line-height: 30px;
  }
  h1, h2 {
      font-weight: normal;
  }
</style>