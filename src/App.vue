<template>
  <div id="app">
    <div class="header">
      <div class="header__title">Cars2go</div>
      <div class="header__button" @click="showModal = true">Add new car</div>
    </div>
    <div class="cars-container">
      <Car
        v-for="car in carList"
        :key="car.id"
        :car="car"
        @delete="deleteCar"/>
    </div>

    <Modal v-if="showModal" @cancel="showModal = false" @submit="addCar">
      <template v-slot:header>
        <span>Add new car</span>
      </template>
      <template v-slot:body>
        <CarForm :new-car.sync="newCar"/>
      </template>
    </Modal>
  </div>
</template>

<script>
import Car from './components/Car.vue'
import Modal from './components/Modal.vue'
import CarForm from './components/CarForm.vue'
import {CARS} from './assets/data.js';

export default {
  name: 'App',
  components: {
    Car,
    Modal,
    CarForm
  },
  data() {
    return {
      carList: CARS,
      showModal: false,
      newCar: {}
    }
  },
  methods: {
    deleteCar(id) {
      this.carList = this.carList.filter((car) => car.id !== id)
    },
    addCar(){
    console.log(this.newCar);
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
