<template>
  <div class="block_alert">
    <div class="body">
      <div class="close_button" @click="close()">x</div>
      <ConfirmDelete v-if="mode == 'delete'" v-on:close="close" v-on:confirmDel="conf"/>
      <EditNote v-if="mode == 'edit'" v-on:close="close" :idEl="getEl()" v-on:retFunc="updatePoint($event)"/>
      <AddNewNote v-if="mode == 'add'" v-on:close="close"/>
    </div>
  </div>
</template>

<script>
import ConfirmDelete from ".//Alerts/ConfirmDelete.vue"
import EditNote from "@/components/Alerts/EditNote";
import AddNewNote from "@/components/Alerts/AddNewNote";

export default {
  name: "AlertPanel",
  props: ['mode', 'idPoint'],
  data() {
    return {
      closeMode: 'close',

    }
  },
  components: {
    ConfirmDelete,
    EditNote,
    AddNewNote
  },
  methods: {
    updatePoint(el) {
      let d = JSON.parse(localStorage.getItem('storedTodos'))
      d[this.idPoint] = el
      localStorage.setItem('storedTodos',JSON.stringify(d))
      this.close()
    },
    close() {
      this.$emit('close')
    },
    conf() {
      this.$emit('confirm', true)
    },
    getEl() {
      return  JSON.parse(localStorage.getItem('storedTodos'))[this.idPoint]
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
