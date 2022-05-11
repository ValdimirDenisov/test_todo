<template>
  <div class="delete_el">
    <h3>Подтвердить действие?</h3>
    <div class="block_button">
      <div class="button red" @click="conf"> Подтвердить </div>
      <div class="button" @click="close()"> Отменить </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "ConfirmDelete",
  methods: {
    conf() {
      this.$emit('confirmDel')
      this.close()
    },
    close() {
        this.$emit('close')
    }
  }
}
</script>

<style scoped lang="sass">
  .delete_el

    .block_button
      display: flex
      justify-content: space-between
      .button
        padding: 10px 20px
        border: 1px solid #000
        cursor: pointer
      .red
        background-color: #ff6800
        color: white

</style>
