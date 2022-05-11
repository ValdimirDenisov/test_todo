<template>
  <div class="block">
    <div class="inp_block">
      <div class="edit" >
        <input type="text" class="inp" v-model="name" placeholder="Название">
      </div>
    </div>

    <div class="checkers">
      <div class="block_r" v-for="(todo, index) in todos" :key="todo">
        <input type="text" @input="updateTodo(index, $event)" :class="inp" placeholder="Что хочу сделать...">
        <div class="buttons">
          <div class="button" @click="addTodo()" v-if="index == todos.length - 1"> + </div>
          <div class="button red" @click="removeTodo(index)" v-if="!((index == todos.length - 1) && (todos.length == 1))" > Удалить </div>
        </div>
      </div>
    </div>

    <div class="block_button">
      <div class="button red" @click="addVote()"> Подтвердить </div>
      <div class="button" @click="close()"> Отменить </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddNewNote",
  data() {
    return {
      name: '',
      todos: [{
        inp: '',
        checked: false
      }]
    }
  },
  methods: {
    addTodo() {
      console.log('reiwirj')
      this.todos.push({
        inp: '',
        checked: false
      })
    },
    removeTodo(id) {
      this.todos.splice(id, 1)
    },

    updateTodo(ind, $event) {
      this.todos[ind].inp = $event.path[0].value
    },
    checkTodos() {
      let flag = false
      if (this.name == '') {
        flag = true
      } else {
        for (let item in this.todos) {
          if (this.todos[item].inp == '') {
            flag = true
            break
          }
        }
      }
      return flag
    },
    addVote() {
      if (this.checkTodos()) {
        alert("Проверьте, все ли поля у вас заполнены")
        return
      }
      let data = JSON.parse(localStorage.getItem('storedTodos'));
      if (data == null) {
        data = []
      }
      let newItem = {
        name: this.name,
        items: this.todos
      }
      data.push(newItem)
      localStorage.setItem('storedTodos', JSON.stringify(data))
      this.todos = []
      this.name = ''
      this.$emit('close')
    },
    close() {
      this.$emit('close')
    }
  }
}
</script>

<style scoped lang="sass">
  .edit
    display: flex
    justify-content: space-between

  .inp
    height: 45px
    width: 300px
    font-size: 20px
    border-radius: 5px
    border: 1px solid #ff6800

  .inp_check
    width: 20px
    height: 20px

  .checkers
    margin: 20px 0
  .inp_block
    margin-top: 25px
  .n_edit
    display: flex
    justify-content: space-between
  .bl
    display: flex
    justify-content: left
    padding-top: 15px
    label
      margin-left: 5px
  .inp_check

  .block_r
    display: flex
    justify-content: space-between
    margin-top: 5px


  .block_button
    display: flex
    justify-content: space-between

  .button
    padding: 10px 20px
    border: 1px solid #000
    cursor: pointer
    display: inline-block
    margin: 5px

  .red
    background-color: #ff6800
    color: white
</style>
