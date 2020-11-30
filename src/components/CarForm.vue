<template>
  <form>
    <label>
      Title
      <input
          type="text"
          v-model="newCar.title"
          placeholder="Title"
      />
    </label>

    <input
        type="text"
        v-model="newCar.price"
        placeholder="Price"
    />
    <input
        type="text"
        v-model="newCar.img"
        placeholder="Url path"
    />
    <input
        type="text"
        v-model="newCar.persons"
        placeholder="Persons"
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
input{
  display:flex;
  margin:8px;
}
</style>