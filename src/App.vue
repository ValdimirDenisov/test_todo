<template>
  <div class="app">
    <h1 class="logo">
      Todo<span class="green">List</span>
    </h1>
    <DivBlock/>
    <div class="conteiner">
      <TodoList v-for="el in els" :key="el" :todo="el" @click="changeCondition()"/>
      <div class="empty_block" v-if="els.length == 0">Добавьте todo, чтобы увидеть список</div>
    </div>
    <AlertPanel v-if="condition" :mode="'confirm_delete'" v-on:close="changeCondition()"></AlertPanel>
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
      els: [
        {
          name: 'Название 1',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
      ],
      condition: true,
    }
  },
  methods: {
    changeCondition() {
      this.condition = (this.condition + 1) % 2
    }
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
