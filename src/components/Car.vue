<template>
  <div class="car">
    <img class="car__img" :src="car.img"/>
    <div class="car__details">
      <div class="car__title">
        {{car.title}}
      </div>
      <div class="flex-row">
        <div class="car__icon-chip"><img class="car__icon-chip__icon" src="@/assets/images/person_icon.png"/><span class="color-light-2">{{car.persons}}</span></div>
        <div class="car__icon-chip"><img class="car__icon-chip__icon" src="@/assets/images/door_icon.png"/>{{car.doors}}</div>
        <div class="car__icon-chip"><img class="car__icon-chip__icon" src="@/assets/images/fuel_icon.png"/>{{car.fuel}}l/100km</div>
      </div>
      <div>
        <div class="car__description">
          <div class="car__description__title">Description</div>
          <div class="color-light-2">{{car.description}}</div>
        </div>
        <div class="car__actions">
          <div class="car__price">${{car.price}}</div>
          <div class="car__dark-button">Book Now</div>
          <div class="car__delete-button" @click.prevent="$emit('delete', car.id)">Delete car</div>
        </div>
      </div>
    </div>
  </div>
</template>

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
  margin-bottom:12px;
  background-color:white;
}
.car__img{
  display:flex;
  width:43%;
  object-fit: contain;
}
.car__details{
  flex-flow:column;
  width:56%;
}
.car__title{
  font-size: 30px;
  font-weight:bold;
  color: var(--color-dark);
  margin:30px 0 20px 0;
}
.car__icon-chip{
  border:solid 1px var(--color-light-2);
  border-radius: 10px;
  padding:5px;
  margin-right:10px;
}
.car__icon-chip__icon{
  height:20px;
  width:20px;
}
.car__description{
  flex-flow: column nowrap;
  width:60%;
  border-right: solid 1px var(--color-light-2);
  padding-right:20px;
}
.car__description__title{
  color: var(--color-dark);
  margin: 20px 0;
}
.car__actions{
  margin-left:20px;
  flex-flow:column nowrap;
}
.car__price{
  color:var(--color-accent);
  font-size:40px;
  font-weight:600;
  margin-bottom: 20px;
}
.car__dark-button{
  background-color: var(--color-dark);
  color: white;
  padding:10px;
  width:150px;
  justify-content: center;
  font-size:20px;
}
.car__delete-button{
  color: var(--color-light-2);
  width:150px;
  justify-content: center;
  padding:10px;
  font-size:14px;
  cursor: pointer;
}
</style>