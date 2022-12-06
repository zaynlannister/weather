<template>
  <div class="header">
    <div class="container">
      <img class="header-logo" src="@/assets/weather-logo.png">
      <search-form v-model="cityName"/>
    </div>
  </div>
  <app-weather :data="weatherDate"/>
</template>

<script>
import SearchForm from "@/components/SearchForm.vue";
import AppWeather from "@/components/AppWeather.vue";

export default {
  components: {
    SearchForm,
    AppWeather
  },

  data() {
    return {
      cityName: "",
      weatherDate: []
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