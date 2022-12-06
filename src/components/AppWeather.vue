<template>
  <div class="container">
    <div class="weather">
      <div class="weather-date">Dec 6, 08:24am</div>
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
    weatherDate: Object
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