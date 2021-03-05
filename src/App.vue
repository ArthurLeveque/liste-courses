<template>
  <div>
  <list-input></list-input>
    <ul>
        <courses-list class="articlesShow" v-for="(product, index) in list" :index="index" :name="product.name" :key="index" @delete-click="removeItem"></courses-list>
    </ul>
  </div>
</template>

<script>
import ListInput from "./components/ListInput";
import CoursesList from './components/CoursesList.vue'

export default {
  name: 'App',
  components: {
    CoursesList,
    ListInput,
  },
  data() {
    return {
      list: [
        {
          name: 'Abricot',
        },

        {
          name: 'ananas',
        },
        
        {
          name: 'patates',
        },
        
        {
          name: 'courgettes',
        },
      ],
    };
  },

  methods: {
    removeItem(i) {
    this.list.splice(i, 1)
    },
  },
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
}

body {
   background-color: rgb(36, 0, 94);
   padding-left: 30px;
   padding-right: 30px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  position: relative;
  margin-top: 60px;
}
</style>
