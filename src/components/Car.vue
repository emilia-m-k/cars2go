<template>
  <div class="car">
    <img class="car__img" :src="car.img"/>
    <div class="car__details">
      <div class="car__title">
        {{car.title}}
      </div>
      <div class="flex-row">
        <div>{{car.persons}}</div>
        <div>{{car.doors}}</div>
        <div>{{car.fuel}}l/100km</div>
      </div>
      <div class="flex-row">
        <div class="flex-column">
          <div>Description</div>
          <div>{{car.description}}</div>
        </div>
        <div class="flex-column">
          <div class="car__price">${{car.price}}</div>
          <button>Book Now</button>
          <button>Delete car</button>
        </div>
      </div>
    </div>
  </div>
</template>
›
<script>
export default {
  name: "Car",
  props: {
    car: {
      type:Object
    }
  }
}
</script>

<style scoped>
.car{
  flex-flow:row nowrap;
  height:400px;
  width:100%;
  margin:10px;
  background-color:white;
}
.car__img{
  display:flex;
  object-fit: contain;
}
.car__details{

}
</style>

