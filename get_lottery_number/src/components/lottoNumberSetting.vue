<template>
  <nav>
    <ul class="lottonumber-setting-list">
      <li class="lottonumber-setting-list-item">
        <span class="btn-make-lottonumber" @click="makeLottoNumber">Make LottoNumber
          <span class="btn-make-lottonumber-icon">
          <i class="fa fa-eercast" aria-hidden="true"></i>
        </span>
      </span>
      </li>
      <li class="lottonumber-setting-list-item" v-if="displaySaveButton">
        <span class="btn-save-lottonumber" @click="saveLottoNumber">Save it!
        <span class="btn-save-lottonumber-icon">
          <i class="fa fa-floppy-o" aria-hidden="true"></i>
        </span>
      </span>
      </li>
    </ul>
  </nav>
</template>
<script>
export default {
  name: "",
  data: function data() {
    return {
      displaySaveButton: false,
    }
  },
  methods: {
    makeLottoNumber() {
      this.$emit("makeLottoNumber");
      this.displaySaveButton = true;
    },
    saveLottoNumber(){
      this.$emit("saveLottoNumber");
      this.displaySaveButton = false;
    }
  }
}
</script>

<style lang="sass">
.make-number-icon
  margin-left: 0.5em

.lottonumber-setting-list
  margin-top: 0.8em
  margin-bottom: 0.8em
  display: flex
  align-items: center
  justify-content: center
  line-height: 2em
  // background-color: #fff

.lottonumber-setting-list-item
  margin-right: 0.8em

.btn-make-lottonumber, .btn-save-lottonumber
  display: inline-block
  background-color: #EDC6A8
  line-height: 2em
  padding-left: 0.5em
  border-radius: 0.3em

.btn-make-lottonumber-icon,.btn-save-lottonumber-icon
  text-align: center
  display: inline-block
  width: 2em
  height: 2em
  border-radius: 0.3em
  line-height: 2em

.btn-make-lottonumber-icon
  background-color: #E2591E

.btn-save-lottonumber-icon
  background-color: #f41212
</style>
