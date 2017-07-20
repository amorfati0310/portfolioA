<template>
<section class="saved-lotto-numbers">
    <div class="saved-lotto-number-box" v-if="savedNumbers.length">
        <ul class="saved-number-list">
            <li v-for=" (savedlottoNumber,index) in savedNumbers" class="saved-lotto-number">

                <span class="each-number">{{savedlottoNumber.numbers}}</span>
                <span class="btn-delete-lottonumber-icon" @click="deleteLottoNumbers(savedlottoNumber,index)">
                  <i class="fa fa-trash-o" aria-hidden="true"></i>
                </span>
                <!--method로 바꾸려는 시도   -->
                <!-- <span class="each-number">{{displayNumbers(savedlottoNumber.numbers)}}</span> -->

                <!--Computed 적용하려 했으나 잘 안 됨   -->
                <!-- <span class="eachnumber" >{{ displayNumbers(savedlottoNumber.numbers)}}</span> -->
                <!-- <span class="each-number" v-text="displayNumbers(savedlottoNumber.numbers)"></span> -->

            </li>
        </ul>
    </div>
    <div class="clear-savedNumber">
      <button class="btn-clearall-savedNumber" @click="allCLear">All Clear</button>
    </div>
</section>
</template>
<script>
export default {
    name: "",
    props: ['savedNumbers'],
    data: function data() {
        return {

        }
    },
    computed: {
        displayNumbers(Numbers) {
            return Numbers;
        }
    },
    methods: {
       displayNumbers() {

      },
      deleteLottoNumbers(savedlottoNumber,index){
        this.$emit('deleteLottoNumbers',savedlottoNumber,index);
        console.log(savedlottoNumber,index);

      },
      allCLear(){
        this.$emit('allCLear')
      }
    },

    updated: function updated() {
        //do something after updating vue instance
        console.log(this.savedNumbers);
    }
}
</script>
<style lang="sass">
.saved-lotto-numbers
  width: 100%
  text-align: center
  line-height: 2.5em
  border-radius: 0.5em

.saved-lotto-number-box
  background-color: #ffeaba

.btn-delete-lottonumber-icon,
  text-align: center
  display: inline-block
  width: 2em
  height: 2em
  border-radius: 0.3em
  line-height: 2em
  color: #cd2015

.clear-savedNumber


.btn-clearall-savedNumber
  border: 0
  background-color: #fff
  padding: 1em
  text-align: center
  color: #cd2015
  border-radius: 0.3em
  margin-top: 1.2em


</style>
