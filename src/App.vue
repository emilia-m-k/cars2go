<template>
  <div id="app">
    <div class="header">
      <div class="header__title">Cars2go</div>
      <div class="header__button">Add new car</div>
    </div>
    <div class="cars-container">
      <Car
        v-for="car in carList"
        :key="car.id"
        :car="car"
        @delete="deleteCar"/>
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
  methods: {
    deleteCar(id) {
      this.carList = this.carList.filter((car) => car.id !== id)
    }
  }
}
</script>

<style>
:root {
  --color-dark:#22313F;
  --color-light-1: #F6F6F6;
  --color-light-2: #A3A3A3;
  --color-accent: #5DAC6E;
}
html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
  font-family: "Roboto", sans-serif;
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
.color-light-2{
  color:var(--color-light-2);
}

#app {
  display:block;
  margin:auto;
  height:100%;
  width:1000px;
}
.header{
  height:100px;
  width:100%;
  justify-content: space-between;
  background-color: var(--color-dark);
  color: var(--color-light-1);
}
.header__title{
  color:var(--color-light-1);
  font-size:20px;
  line-height:100px;
  margin-left:20px;
}
.header__button{
  line-height: 100px;
  color: var(--color-light-1);
  margin-right:20px;
  cursor: pointer;
  font-size:16px;
}
.cars-container{
  flex-flow: column nowrap;
  background-color: var(--color-light-1);
  padding:12px;
  min-height:100%;
}
</style>
