<template>
  <div>
    <h1>Liste de courses</h1>
    <list-input @name="addItem"></list-input>
    <ul>
        <courses-list 
        v-for="(item, index) in list" 
        :index="index" :item="item" 
        :key="index" 
        @delete-click="removeItem" 
        @click="check(index)"
        :class="['articlesShow', {checked : item.checked}]">
        </courses-list>
    </ul>
    <button class="delete" @click="deleteAll">Supprimer la liste</button>
  </div>
  <confirm-delete v-if="showConfirm" @cancel="cancel" @confirm="confirm"></confirm-delete>
</template>

<script>
import CoursesList from './components/CoursesList.vue'
import ConfirmDelete from './components/ConfirmDelete.vue';
import ListInput from './components/ListInput.vue';

export default {
  name: 'App',
  components: {
    CoursesList,
    ConfirmDelete,
    ListInput,
  },
  data() {
    return {
      list: [],
      showConfirm: false
    };
  },
  mounted() {
    if(localStorage.getItem('list')) {
      try {
        this.list = JSON.parse(localStorage.getItem('list'));
      } catch(e) {
        localStorage.removeItem('list');
      }
    }
  },
  methods: {
    removeItem(i) {
      this.list.splice(i, 1);
      this.saveList();
    },
    addItem(name) {
      const item = {
        name: name,
        checked: false
      }
      this.list.push(item);
      this.saveList();
    },
    saveList() {
      let parsed = JSON.stringify(this.list);
      localStorage.setItem('list', parsed);
    },
    deleteAll() {
      this.showConfirm = true;
    },
    cancel() {
      this.showConfirm = false;
    },
    confirm() {
      this.list.forEach(element => {
        this.list.splice(element);
      });
      this.saveList();
      this.showConfirm = false;
    },
    check(index) {
      this.list[index].checked = !this.list[index].checked;
      this.saveList();
    }
  },
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
}

body {
  position: relative;
  background-color: rgb(36, 0, 94);
}

h1 {
  margin-bottom: 20px;
}

ul {
  max-width: 100vw;
}

.delete {
  padding: 5px;
  border-radius: 0px;
  margin: 10px 0;
}

.checked div p{
  text-decoration: line-through;
  color: grey;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  position: relative;
  margin-top: 20px;
  padding-bottom: 80px;
}
</style>
