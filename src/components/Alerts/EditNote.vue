<template>
  <div class="block">
    <div class="inp_block">
      <div class="edit" v-if="false">
        <input type="text" class="inp">
        <div class="button"> Ок </div>
      </div>
      <div class="edit" >
        <h3>Название</h3>
        <div class="button"> Изменить </div>
      </div>
    </div>

    <div class="checkers">

      <div class="block_r" >
        <div class="bl">
          <input type="checkbox" class="inp_check">
          <label for="">ffklgwerk;ll'sfgl'</label>
        </div>
        <div class="buttons">
          <div class="button"> Изменить </div>
          <div class="button red"> Удалить </div>
        </div>
      </div>

      <div class="block_r" v-if="false">
        <input type="text" class="inp">
        <div class="buttons">
          <div class="button"> Ок </div>
          <div class="button red"> Удалить </div>
        </div>
      </div>
    </div>

    <div class="block_button">
      <div class="button red"> Подтвердить </div>
      <div class="button" @click="close()"> Отменить </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "EditNote",
  components: {},
  methods: {
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
