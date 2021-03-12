<template>
  <div class="message">
    <p>Voulez vous vraiment supprimer ?</p>
    <div class="flex">
      <button @click="cancel">Non</button>
      <button @click="confirm">Oui</button> 
    </div>
  </div>
  <div class="background"></div>
</template>

<script>
export default {
  emits: ['cancel', 'confirm'],
  methods: {
  cancel() {
    this.$emit('cancel');  
  },
  confirm() {
    this.$emit('confirm');  
  },
}, 
}
</script>

<style scoped>
  .message{
    z-index: 2;
    position: fixed;
    top : calc(50vh  - 60px);
    left: calc(50vw  - 110px);
    background-color: white;
    padding: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    color: black;
    width: 200px;
    height: 100px;
  }
  .background{
    z-index: 1;
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100vw;
    content: '';
    background-color:black;
    opacity: 0.3;
  }
  p{
    margin-bottom: 30px;
  }
  .flex{
    width: 100%;
    display: flex;
    justify-content: space-around;
  }

  button {
    padding: 5px;
    border-radius: 0px;
    margin: 10px 0;
  }
</style>