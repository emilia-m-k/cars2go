<template>
  <div id="app">
    <div class="header">
      <div class="header__title">Cars2go</div>
      <div class="header__button" @click="showModal = true">Add new car</div>
    </div>
    <form class="search-bar" @submit.prevent="filterCarList">
      <input
        class="search-bar__input"
        type="text"
        v-model="search"
        placeholder="Search"
      />
      <button class="button button--dark search-bar__button" @click="filterCarList">Search</button>
    </form>
    <div class="cars-container">
      <div class="cars-container__empty" v-if="!filteredCarList.length && carList.length">
        Your search did not match any car.
      </div>
      <div class="cars-container__empty" v-if="!carList.length">
        Car list is empty.
      </div>
      <Car
        v-for="car in filteredCarList"
        :key="car.id"
        :car="car"
        @delete="deleteCar"/>
    </div>

    <Modal v-if="showModal" @cancel="cancel" @submit="addCar">
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
import Car from './components/Car.vue';
import Modal from './components/Modal.vue';
import CarForm from './components/CarForm.vue';
import {CARS} from './assets/data.js';

let nextId = 5;
function createCar(data){
  return {
    id: nextId++,
    title: data.title,
    price: data.price,
    img: data.img,
    persons: data.persons,
    doors: data.doors,
    fuel: data.fuel,
    description: data.description
  };
}

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
      filteredCarList: CARS,
      showModal: false,
      newCar: {},
      search: ""
    }
  },
  methods: {
    deleteCar(id) {
      this.carList = this.carList.filter((car) => car.id !== id);
      this.filterCarList();
    },
    cancel(){
      this.showModal= false;
      this.newCar={};
    },
    addCar(){
      this.carList.push(createCar(this.newCar));
      this.filterCarList();
      this.cancel();
    },
    filterCarList(){
      this.filteredCarList = this.carList.filter((car) => car.title.toLowerCase().includes(this.search.toLowerCase()))
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
.button {
  border: solid 1px var(--color-dark);
  border-radius: 3px;
  background-color: white;
  padding:10px;
  width:100px;
}
.button--dark {
  background-color: var(--color-dark);
  color:var(--color-light-1);
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
.search-bar{
  display:flex;
}
.search-bar__input{
  background: white url(./assets/images/search_icon.png) left no-repeat;
  background-size:25px 25px;
  display:flex;
  flex-grow: 1;
  border: solid 1px var(--color-light-2);
  border-radius:3px;
  padding:6px 6px 6px 26px;
  margin:20px;
}
.search-bar__button{
  margin: 20px 20px 20px 0;
  font-size:14px;
}
.cars-container__empty{
  color:var(--color-dark);
  justify-content: center;
  margin-top:20px;
}
.cars-container{
  flex-flow: column nowrap;
  background-color: var(--color-light-1);
  padding:12px;
  min-height:100%;
}
</style>
