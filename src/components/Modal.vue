<template>
  <div class="modal-backdrop" id="modal-template">
    <div class="modal">
      <div class="modal__header">
        <slot name="header"></slot>
      </div>
      <div class="modal__body">
        <slot name="body"></slot>
      </div>
      <div class="modal__footer">
        <button class="modal__button" @click="$emit('cancel')">
          Cancel
        </button>
        <button class="modal__button modal__button--dark" @click.prevent="$emit('submit')">
          Submit
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal"
}
</script>

<style scoped>
.modal-backdrop {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  /*display: table;*/
  transition: opacity 0.3s ease;
}
.modal {
  width: 600px;
  margin: 0px auto;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  flex-flow: column nowrap;
  position:fixed;
  top:50%;
  left:50%;
  transform:translate(-50%, -50%);
  color: var(--color-dark);
}
.modal__header{
  padding:20px;
  border-bottom: solid 1px var(--color-light-2);
  font-size:20px;
}
.modal__body {
  padding:20px;
}
.modal__footer {
  padding:20px;
  justify-content: space-between;
}
.modal__button {
  border: solid 1px var(--color-dark);
  border-radius: 3px;
  background-color: white;
  padding:10px;
  width:100px;
}
.modal__button--dark {
  background-color: var(--color-dark);
  color:var(--color-light-1);
}
</style>