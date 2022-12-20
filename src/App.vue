<template>
  <div class="header">
    <div class="container">
      <img class="header-logo" src="@/assets/weather-logo.png">
      <search-form @click="getGeoOfCity" v-model="cityName"/>
    </div>
  </div>
  <app-weather
    :date="date"
    :cityName="cityName"
  />
</template>

<script>
import SearchForm from "@/components/SearchForm.vue";
import AppWeather from "@/components/WeatherData.vue";

export default {
  components: {
    SearchForm,
    AppWeather
  },

  data() {
    return {
      cityName: "",
      weatherDate: {},
      apiKey: "265a6bf77fad2b8dce59e0abce8a30d7",
      date: new Date()
    }
  },

  methods: {
    isValidInput() {
      return this.cityName.trim().length !== 0;
    },

    getGeoOfCity() {
      if (this.isValidInput()) {
        const url = `http://api.openweathermap.org/geo/1.0/direct?q=${this.cityName}&limit=1&appid=${this.apiKey}`

        try {
          fetch(url)
              .then(response => {
                return response.json()
              })
              .then(data => {
                if (data.length !== 0) {
                  this.fetchWeatherDate(data)
                } else {
                  alert("Город не найден")
                }
              })
        } catch (err) {
          console.error(err)
        }
      }
    },

    fetchWeatherDate(city) {
      // const url = `https://api.openweathermap.org/data/2.5/weather?lat=${city[0].lat}&lon=${city[0].lon}&appid=${this.apiKey}`
      //
      // try {
      //   fetch(url)
      //       .then(response => {
      //         return response.json()
      //       })
      //       .then(data => {
      //         this.weatherDate = data;
      //         console.log(this.weatherDate)
      //       })
      // } catch (err) {
      //   console.log(err)
      // }
    }
  }
}
</script>

<style>
  .container {
    width: 1080px;
    margin: 0 auto;
  }

  .header {
    background-color: #ededed;
  }

  .header-logo {
    width: 50px;
    height: 50px;
    margin-right: 20px;
  }

  .header .container {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px 0;
  }
</style>