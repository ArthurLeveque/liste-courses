<template>
  <list-input></list-input>
</template>

<script>
  import ListInput from "./components/ListInput";

  export default {
    name: 'App',
    components: {
      ListInput
    }
  }
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }

  #app {
    position: relative;
  }
</style>