<template>
  <div class="app">
    <h1 class="logo">
      Todo<span class="green">List</span>
    </h1>
    <DivBlock v-on:add="addItem()"/>
    <div class="conteiner">
      <TodoList v-for="(el, index) in els" :key="el" :todo="el" :id="index" v-on:edit="editItem($event)" v-on:del="delItem($event)"/>
      <div class="empty_block" v-if="els.length == 0">Добавьте todo, чтобы увидеть список</div>
    </div>
    <AlertPanel v-if="condition" v-on:confirm="delEl($event)" :idPoint="id" :mode="mode_alert" v-on:close="changeCondition()"></AlertPanel>
  </div>
</template>

<script>
import TodoList from ".//components/todo.vue"
import DivBlock from ".//components/diviver.vue"
import AlertPanel from ".//components/AlertPanel.vue"

export default {
  name: 'App',
  components: {
    TodoList,
    DivBlock,
    AlertPanel
  },
  data() {
    return {
      get els() {
        let t = JSON.parse(localStorage.getItem('storedTodos'))
        if (t == null) {
          t = {}
        }
        return t
      },
      condition: false,
      mode_alert: '',
      edit_id: undefined,
      id: ''
    }
  },
  methods: {
    changeCondition() {
      if (this.condition == true) {
        this.condition = false
      } else {
        this.condition = true
      }
    },
    delEl(a) {
      console.log(a)
      if (a) {
        let data = this.els
        data.splice(this.id, 1)
        localStorage.setItem('storedTodos',JSON.stringify(data))
      } else {
        this.id = null
      }
    },
    delItem(id) {
      this.id = id
      this.mode_alert = 'delete'
      this.changeCondition()
    },
    editItem(id) {
      this.id = id
      this.mode_alert = 'edit'
      this.changeCondition()
    },
    addItem() {
      this.mode_alert = 'add'
      this.changeCondition()
    },
  }
}
</script>

<style lang="sass">
  .app
    font-family: 'Open Sans', sans-serif
    text-align: center
    .logo
      font-size: 70px
      .green
        color: #51f651
    .conteiner
      width: 100%
      flex-wrap: wrap
      display: flex
      justify-content: center
      align-items: flex-start

</style>
