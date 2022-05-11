<template>
  <div class="block">
    <div class="inp_block">
      <div class="edit" v-if="!nameVis">
        <input type="text" class="inp" v-model="ans.name">
        <div class="button" @click="changeName()"> Ок </div>
      </div>
      <div class="edit" v-if="nameVis">
        <h3>{{ ans.name }}</h3>
        <div class="button" @click="changeName()"> Изменить </div>
      </div>
    </div>

    <div class="checkers" v-for="(el, index) in ans.items" :key="el">
      <div v-if="!removedes[index]">
      <div class="block_r" v-if="!editeble[index]">
        <div class="bl">
          <input type="checkbox" class="inp_check" v-model="el.checked">
          <label for="">{{ el.inp}}</label>
        </div>
        <div class="buttons">
          <div class="button" @click="changeValue(index)"> Изменить </div>
          <div class="button red" @click="delElement(index)"> Удалить </div>
        </div>
      </div>

      <div class="block_r" v-if="editeble[index]">
        <input type="text" class="inp" v-model="el.inp">
        <div class="buttons">
          <div class="button" @click="confirmChangeValue(index)"> Ок </div>
          <div class="button red" @click="delElement(index)"> Удалить </div>
        </div>
      </div>
      </div>
    </div>

    <div class="block_button">
      <div class="button red" @click="saveSetting()"> Подтвердить </div>
      <div class="button" @click="close()"> Отменить </div>
    </div>
    <ConfirmComponent v-if="condition" v-on:close="closer" v-on:confirm="delEl($event)"/>
  </div>
</template>

<script>
import ConfirmComponent from '@/components/ConfirmComponent'

export default {
  name: "EditNote",
  props: ['idEl'],
  data() {
    return {
      editeble: {},
      nval: {},
      name: this.idEl.name,
      nameVis: true,
      condition: false,
      id: null,
      removedes: {},
      edites: [],
      pos: null,
      mode: false,
      ans: undefined

    }

  },
  components: {
    ConfirmComponent
  },
  methods: {
    saveSetting() {
      let ne = {
        name: this.ans.name,
        items: []
      }
      for (let a in this.ans.items) {
        // console.log(this.ans.items[a])
        if (!this.removedes[a]) {
          ne.items.push(this.ans.items[a])
        }
      }
      this.$emit('retFunc', ne)
    },
    delEl(a) {
      if (a) {
        if (this.mode) {
          this.mode = false
          this.$emit('close')
        } else {
          if (this.pos != null) {
            this.edites.splice(this.pos, this.edites.length - this.pos)
            console.log(this.edites)
          }
          this.removedes[this.id] = true
          this.edites.push({
            event: 'del',
            ind: this.id
          })
          if (this.pos != null) this.pos = null
        }
      }
    },

    delElement(ind) {
      this.id = ind
      this.condition = true
    },
    closer() {
      this.condition = false
    },
    changeName() {
      if (this.nameVis) {
        this.nameVis = false
      } else {
        this.nameVis = true
      }
    },
    confirmChangeValue(ind) {
      this.editeble[ind] = false

    },
    changeValue(ind) {
      this.editeble[ind] = true
    },
    close() {
      this.condition = true
      this.mode = true

    },
    onKeyPress(e) {
      if (e.charCode == 26 && !e.shiftKey && e.ctrlKey) {
        if (this.pos == null) {
          this.pos =  this.edites.length - 1
        }
        this.removedes[this.edites[this.pos].ind] = false
        this.pos -= 1
        if (this.pos < 0) {
          this.pos = 0
        }
      }
      if (e.charCode == 26 && e.shiftKey && e.ctrlKey) {
        this.removedes[this.edites[this.pos].ind] = true
        this.pos += 1
        if (this.pos > this.edites.length - 1) {
          this.pos = this.edites.length - 1
        }
      }
    },
  },
  created() {
    document.addEventListener('keypress', this.onKeyPress);
    this.ans = this.idEl
  },
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
