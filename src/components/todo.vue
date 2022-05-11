<template>
  <div class="todo" @click="editEl()">
    <div class="deleter" @click="deleteEl()"><img src="../assets/delete.png" alt="" class="deleter_img"></div>
    <h1>{{ todo.name }}</h1>
    <ul class="todo_list" >
      <span v-for="(item, index) in todo.items" :key="item">
        <li  :class="{dchecked: !item.checked}" v-if="index < 3">{{ item.inp }}</li>
      </span>

    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: ['todo', 'id'],
  data() {
    return {
      req: undefined
    }
  },
  methods: {
    deleteEl() {
      this.req = true
      this.$emit('del', this.id)
    },
    editEl() {
      if (this.req) {
        this.req = false
      } else {
        this.$emit('edit', this.id)
      }
    }
  }
}
</script>

<style scoped lang="sass">
  .dchecked
    list-style-type: circle
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
