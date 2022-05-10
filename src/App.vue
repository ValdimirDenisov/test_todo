<template>
  <div class="app">
    <h1 class="logo">
      Todo<span class="green">List</span>
    </h1>
    <div class="block_diviver">
      <div class="head">Список задач</div>
      <hr class="diviver">
      <div class="add_button">+</div>
    </div>
    <div class="conteiner">
      <TodoList v-for="el in els" :key="el" :todo="el"/>
      <div class="empty_block" v-if="els.length == 0">Добавьте todo, чтобы увидеть список</div>
    </div>
  </div>
</template>

<script>
import TodoList from ".//components/todo.vue"

export default {
  name: 'App',
  components: {
    TodoList,
  },
  data() {
    return {
      els: [
        {
          name: 'Название 1',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
        {
          name: 'Название 2',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
        {
          name: 'Название 3',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
        {
          name: 'Название 4',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
        {
          name: 'Название 5',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
        {
          name: 'Название 6',
          items: [',fjgsijkn;f', 'dkjirjegtjinios', 'sfjdijgel']
        },
      ]
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

    .block_diviver
      display: flex
      justify-content: center
      align-items: center
      .head
        display: inline-block
        vertical-align: middle
        font-size: 20px
        margin-right: 20px

      .diviver
        width: 70%
        display: inline-block
        vertical-align: middle
        border: 2px dashed #000
        margin: 0 20px
        margin-top: 3px

      .add_button
        display: inline-block
        vertical-align: middle
        font-size: 40px
        cursor: pointer

    .conteiner
      width: 100%
      flex-wrap: wrap
      display: flex
      justify-content: center
      align-items: flex-start

</style>
