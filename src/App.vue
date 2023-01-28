<template>
  <div class="header">
    <div class="container">
      <img class="header-logo" src="@/assets/weather-logo.png">
      <search-form
        @search="getGeoOfCity"
        v-model="cityName"
        :isLoading="isLoading"
      />
    </div>
  </div>

  <div class="container" v-if="isLoading">
    <div class="loading">Loading...</div>
  </div>
  <weather-data
    v-else
    :date="date"
    :cityName="cityName"
    :weatherData="weatherData"
  />
</template>

<script>
import SearchForm from "@/components/SearchForm.vue";
import WeatherData from "@/components/WeatherData.vue";

export default {
  components: {
    WeatherData,
    SearchForm,
  },

  data() {
    return {
      cityName: "",
      weatherData: {},
      apiKey: "265a6bf77fad2b8dce59e0abce8a30d7",
      date: new Date(),
      isLoading: false
    }
  },

  methods: {
    isValidInput() {
      return this.cityName.trim().length !== 0;
    },

    getGeoOfCity() {
      if (this.isValidInput()) {
        this.isLoading = true;

        const url = `http://api.openweathermap.org/geo/1.0/direct?q=${this.cityName}&limit=1&appid=${this.apiKey}`;

        try {
          fetch(url)
              .then(response => {
                return response.json();
              })
              .then(data => {
                if (data.length !== 0) {
                  this.fetchWeatherDate(data);
                  this.isLoading = false;
                } else {
                  alert("Город не найден");
                }
              })
        } catch (err) {
          console.error(err);
        }
      }
    },

    fetchWeatherDate(city) {
      const url = `https://api.openweathermap.org/data/2.5/weather?lat=${city[0].lat}&lon=${city[0].lon}&appid=${this.apiKey}`;

      try {
        fetch(url)
            .then(response => {
              return response.json();
            })
            .then(data => {
              this.weatherData = data;
              this.weatherData = Object.assign({}, this.weatherData, data);
            })
      } catch (err) {
        console.log(err);
      }
    }
  }
}
</script>

<style>
  .container {
    width: 1080px;
    margin: 0 auto;
    padding: 0 20px;
  }

  .header {
    border-bottom: 1px solid #b6b6b6;
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
    padding: 20px;
  }

  .loading {
    padding-top: 10px;
  }

  @media (max-width: 1150px) {
    .container {
      width: unset;
    }
  }

  @media (max-width: 1500px) {
    html body {
      background-size: unset;
    }
  }
</style>