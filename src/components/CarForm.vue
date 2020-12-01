<template>
  <form class="car-form">
    <label for="new-car-title" class="car-form__label">Title</label>
    <input
      class="car-form__input"
      id="new-car-title"
      type="text"
      v-model="newCar.title"
      placeholder="Title"
    />
    <label for="new-car-price" class="car-form__label">Price</label>
    <input
      class="car-form__input"
      id="new-car-price"
      type="text"
      v-model="newCar.price"
      placeholder="Price"
    />
    <label for="new-car-img" class="car-form__label">Image URL</label>
    <input
      class="car-form__input"
      id="new-car-img"
      type="text"
      v-model="newCar.img"
      placeholder="Image URL"
    />
    <div class="car-form__container">
      <div class="flex-column">
        <label for="new-car-persons" class="car-form__label">Persons</label>
        <input
          class="car-form__input"
          id="new-car-persons"
          type="text"
          v-model="newCar.persons"
          placeholder="Persons"
        />
      </div>
      <div class="flex-column">
        <label for="new-car-doors" class="car-form__label">Doors</label>
        <input
          class="car-form__input"
          id="new-car-doors"
          type="text"
          v-model="newCar.doors"
          placeholder="Doors"
      />
      </div>
      <div class="flex-column">
      <label for="new-car-fuel" class="car-form__label">Litres per 100 km</label>
        <input
          class="car-form__input"
          id="new-car-fuel"
          type="text"
          v-model="newCar.fuel"
          placeholder="Litres per 100 km"
        />
      </div>
    </div>
    <label for="new-car-description" class="car-form__label">Description</label>
    <textarea
      class="car-form__input car-form__textarea"
      id="new-car-description"
      v-model="newCar.description"
      placeholder="Description"
      rows="8"
    />
  </form>
</template>

<script>
export default {
  name: "Form",
  props: {
    newCar: {
      type:Object
    }
  }
}
</script>

<style scoped>
.car-form{
  display:flex;
  flex-flow:column nowrap;
  width:100%;
}
.car-form__container{
  flex-flow:row nowrap;
  justify-content: space-between;
}
.car-form__label{
  display:flex;
  margin-bottom:6px;
}
.car-form__input{
  display:flex;
  margin-bottom:20px;
  border: solid 1px var(--color-light-2);
  border-radius:3px;
  padding: 6px 6px 6px 10px;
}
.car-form__textarea{
  font-family: "Roboto", sans-serif;
}
</style>