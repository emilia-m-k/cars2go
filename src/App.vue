<template>
  <div id="app">
    <div class="header">
      <div class="header__title">Cars2go</div>
      <button class="header__button">Add new car</button>
    </div>
    <div class="cars-container">
      <Car
        v-for="car in carList"
        :key="car.id"
        :car="car"/>
    </div>
  </div>
</template>

<script>
import Car from './components/Car.vue'
import {CARS} from './assets/data.js';

export default {
  name: 'App',
  components: {
    Car,
  },
  data() {
    return {
      carList: CARS,
    }
  },
}
</script>

<style>
html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
}
div {
  display:flex;
}
.flex-row{
  flex-direction: row;
}
.flex-column{
  flex-direction:column;
}

#app {
  display:block;
  margin:auto;
  height:100%;
  width:1200px;
}
.header{
  height:100px;
  width:100%;
  justify-content: space-between;

}
.cars-container{
  flex-flow: column nowrap;
}
</style>
