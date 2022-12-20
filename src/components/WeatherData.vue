<template>
  <div class="container" v-if="weatherData.main">
    <div class="weather">
      <div class="weather-date">{{ date.toLocaleString() }}</div>
      <div class="weather-city">{{ weatherData.name }}</div>
      <div class="weather-temp">
        <img src="@/assets/clouds.svg">
        <span>{{ kelvinToCelsius(weatherData.main.temp) }}°C</span>
      </div>
      <div class="weather-info">Fells like {{ kelvinToCelsius(weatherData.main.feels_like) }}°C. {{ weatherData.weather[0].description }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    date: Object,
    cityName: String,
    weatherData: Object
  },

  data() {
    return {
      temp: Number
    }
  },

  methods: {
    kelvinToCelsius(temp) {
      return (temp - 273).toFixed(0)
    }
  }
}
</script>

<style scoped>
  .weather {
    padding-top: 20px;
  }

  .weather-date {
    color: #eb6e4b;
  }

  .weather-city {
    font-size: 24px;
    font-weight: bold;
  }

  .weather-temp {
    display: flex;
    align-items: center;
    font-size: 30px;
    font-weight: 500;
    margin: 10px 0 10px;
  }

  .weather-temp img {
    width: 40px;
    height: 40px;
    margin-right: 8px;
  }

  .weather-info {
    font-weight: 500;
  }
</style>