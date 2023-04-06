<script setup>
import api from "./services/api"
import SearchBox from "./components/SearchBox.vue"
import WeatherCard from "./components/WeatherCard.vue"
import { ref } from "vue"

const weather = ref({})
const weatherList = ref([])
const showWeather = ref(false)

const onSearch = (query) => {
  weather.value = fetchWeather(query);
}

const fetchWeather = (query) => {
  api.get(`/current.json?key=${import.meta.env.VITE_API_KEY}&q=${query}`)
  .then(res => {
    weather.value = res.data;
    showWeather.value = true
  })
  .catch(res => {
    showWeather.value = false
  })
}

const addTolist = (weather) => {
  console.log(weather);
  weatherList.value.append(weather)
}

</script>

<template>
  <main id="app">
    <div class="container">
      <SearchBox @search="onSearch"/>
      <WeatherCard :weather="weather" v-if="showWeather" @add="addTolist"/>
    </div>
  </main>
</template>

<style scoped>
#app {
  background-color: lightblue;
}

.container {
  min-height: 100vh;
  width: 40%;
  margin: 0 auto;
  padding: 2em 0;
}

</style>
