<script setup>
import { computed } from '@vue/reactivity'

const props = defineProps(['weather'])

const location = computed(() => {
  return `${props.weather.location.name}, ${props.weather.location.country}`
})

</script>

<template>
  <div class="weather-wrap">
    <div class="location-box">
      <div class="location">
        <span>{{ location }}</span>
      </div>
    </div>

    <div class="weather-box">
      <div class="temp">
        <span>{{ weather.current.temp_c }}°C</span>
      </div>

      <div class="weather">
        <span>{{ weather.current.condition.text }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.weather-wrap {
  border: 3px solid white;
  width: fit-content;
  margin: 0 auto;
  padding: 3em 1em;
  border-radius: 2em;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0;

  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #fff;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box svg {
  margin: 0.3em 0 0 0;
  color: white;
  cursor: pointer;
}
</style>
