<template>
  <div class="container">
    <div class="weather">
      <div class="weather-date">{{ date }}</div>
      <div class="weather-city">London</div>
      <div class="weather-temp">
        <img src="@/assets/clouds.svg">
        <span>3°C</span>
      </div>
      <div class="weather-info">Fells like 2°C. Broken clouds. Light air</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    date: Object,
    cityName: String
  },

  data() {
    return {
      weatherDate: {}
    }
  },

  methods: {
    kelvinToCelsius(temp) {
      return temp - 273;
    },

    fetchWeatherDate(city) {
      const url = `https://api.openweathermap.org/data/2.5/weather?lat=${city[0].lat}&lon=${city[0].lon}&appid=${this.apiKey}`

      try {
        fetch(url)
            .then(response => {
              return response.json()
            })
            .then(data => {
              this.weatherDate = data;
            })
      } catch (err) {
        console.log(err)
      }
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