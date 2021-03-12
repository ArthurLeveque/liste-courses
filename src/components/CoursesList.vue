<template>
<li>
    <div class="courses-list">
        <p>{{ name }}</p>
        <button @click="triggerDeleteClick">x</button>
    </div>
    <hr>
</li>
</template>

<script>

export default {
    props : ['name', 'index'],
    emits : ['deleteClick'],
    methods : {
       triggerDeleteClick() {
         this.$emit('deleteClick', this.index)
      },
    },
}
</script>

<style scoped>
li {
  list-style-type: none;
  margin: 10px 10px;
}
p{
  text-align: left;
  width: 90%;
  word-wrap: break-word;
}
hr {
  margin-top: 10px;
}
.courses-list {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
button {
  margin-left: 15px;
  font-size: 25px;
  color: red;
  background: none;
  border: none;
}
</style>
