<template>
  <section>
    <nav v-if="giveLottoNumber.length" class="lotto-number-box">
      <ul  class="lotto-number-list">
        <li v-for="lottoNumber in giveLottoNumber" class="lotto-number">{{lottoNumber}}</li>
      </ul>
    </nav>
  </section>
</template>
<script>
export default {
  name: "",
  props:['giveLottoNumber'],
  data: function data() {
    return {

    }
  }
}
</script>
<style lang="sass">
.lotto-number-box
  display: flex
  align-items: center
  justify-content: center
  background-color: #fff
  padding: 0.8em
  border-radius: 0.5em

.lotto-number-list
  text-align: center

.lotto-number
   border-radius: 50%
   width: 3em
   height: 3em
   line-height: 3em
   display: inline-block
   position: relative
   text-align: center
   background-color: #AB2E3E
   color: #fff
   margin-right: 10px

// .add-lotto, .remove-lotto
//   text-align: center
//   display: inline-block
//   width: 2em
//   height: 2em
//   line-height: 2em
//   background-color: #FFAD02
//   color: #fff
//   border-radius: 0.3em
//   margin-right: 0.3em

</style>
