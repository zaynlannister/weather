<template>
    <div class="header">
      <div class="container">
        <img class="header-logo" src="@/assets/weather-logo.png">
        <div>
          <input class="input" type="text" placeholder="Search city">
          <button class="button">Search</button>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {

    }
  }
}
</script>

<style scoped>
  .container {
    width: 1080px;
    margin: 0 auto;
  }

  .input {
    width: 400px;
    border: 1px solid #fff;
    outline: none;
    padding: 8px 15px;
    border-bottom-left-radius: 5px;
    border-top-left-radius: 5px;
    transition: 100ms all;
  }

  .input:focus {
    border-color: #48484a;
  }

  .button {
    cursor: pointer;
    background-color: #48484a;
    color: #fff;
    border: 1px solid #48484a;
    outline: none;
    padding: 8px 10px;
    border-bottom-right-radius: 5px;
    border-top-right-radius: 5px;
    transition: 100ms all;
  }

  .button:hover {
    background-color: #717070;
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