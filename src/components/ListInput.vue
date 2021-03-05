<template>
  <div>
    <input v-model="name" @keypress.enter="addItem" type="text">
    <button @click="addItem">+</button>
  </div>
</template>

<script>
  export default {
    emits: ['name'],
    data() {
      return {
        name: '',
      }
    },
    methods: {
      updateUsername() {
        this.$emit('name', this.nameValue);
      }
    },  
  }
</script>

<style scoped>
  div{
    display: flex;
    align-items: center;
    justify-content: space-evenly;

    position: fixed;
    bottom: 0;
    width: 100%;
    background: #ebebeb;
    padding: 10px 0;
  }
  input{
    width: 70%;
    padding: 10px;
  }
  button{
    width: 20%;
    padding: 10px;
  }
</style>