<template>
  <div class="block_alert">
    <div class="body">
      <div class="close_button" @click="close()">x</div>
      <ConfirmDelete v-on:close="close"/>
    </div>
  </div>
</template>

<script>
import ConfirmDelete from ".//Alerts/ConfirmDelete.vue"
export default {
  name: "ConfirmComponent",
  props: ['mode'],
  data() {
    return {
      closeMode: 'close'
    }
  },
  components: {
    ConfirmDelete
  },
  methods: {
    close() {
      this.$emit('close')
    }
  }
}
</script>

<style scoped lang="sass">
.block_alert
  width: 100%
  height: 100%
  position: absolute
  left: 0
  top: 0
  background-color: rgba(17, 17, 17, 0.33)
  .body
    padding: 20px
    border-radius: 15px
    width: 600px
    background-color: #fff
    position: absolute
    left: calc(50% - 300px)
    top: calc(50% - 300px)
    .close_button
      position: absolute
      right: 20px
      top: 0px
      cursor: pointer
      font-size: 25px
      color: red
</style>
