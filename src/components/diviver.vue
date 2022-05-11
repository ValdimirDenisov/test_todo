<template>
  <div class="block_diviver">
    <div class="head">Список задач</div>
    <hr class="diviver">
    <div class="add_button" @click="addEvent()">+</div>
  </div>
</template>

<script>
export default {
  name: "DivBlock",
  methods: {
    addEvent() {
      this.$emit('add')
    }
  }
}
</script>

<style scoped lang="sass">
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
</style>
