<template>
  <div class="block">
    <div class="inp_block">
      <div class="edit" >
        <input type="text" class="inp" placeholder="Название">
      </div>
    </div>

    <div class="checkers">
      <div class="block_r">
        <input type="text" class="inp" placeholder="Что хочу сделать...">
        <div class="buttons">
          <div class="button"> + </div>
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
  name: "AddNewNote"
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
