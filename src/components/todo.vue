<template>
  <div class="todo">
    <a href="" class="deleter"><img src="../assets/delete.png" alt="" class="deleter_img"></a>
    <h1>{{ todo.name }}</h1>
    <ul class="todo_list" >
      <li v-for="item in todo.items" :key="item">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: ['todo']
}
</script>

<style scoped lang="sass">
  .todo
    padding: 20px
    background-color: #e3e3e3
    width: 300px
    text-align: center
    font-family: 'Open Sans', sans-serif
    margin: 5px
    cursor: pointer
    .todo_list
      text-align: left
    .deleter
      text-align: right
    .deleter_img
      display: none
      width: 30px

  .todo:hover
    .deleter_img
      display: block
    h1
      margin-top: -7px

</style>
