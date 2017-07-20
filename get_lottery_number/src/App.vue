<template>
  <div id="app">
    <lottoHeader></lottoHeader>
    <lottoNumberSetting v-on:makeLottoNumber="makeLottoNumber" v-on:saveLottoNumber="saveLottoNumber"></lottoNumberSetting>
    <lottoNumberList :giveLottoNumber="lottoNumbers"></lottoNumberList>
    <lottoNumberSaveList :savedNumbers="savedNumbers" v-on:deleteLottoNumbers="deleteLottoNumbers"
     v-on:allCLear="allCLear"
    ></lottoNumberSaveList>
    <lottoFooter></lottoFooter>
  </div>
</template>

<script>
import lottoHeader from './components/lottoHeader.vue'
import lottoNumberSetting from './components/lottoNumberSetting.vue'
import lottoNumberList from './components/lottoNumberList.vue'
import lottoNumberSaveList from './components/lottoNumberSaveList.vue'
import lottoFooter from './components/lottoFooter.vue'
export default {
  name: 'app',

  data () {
    return {
      lottoNumbers:[],
      savedNumbers:[],
      index:0

    }
  },
  components: {
    lottoHeader: lottoHeader,
    lottoNumberSetting: lottoNumberSetting,
    lottoNumberList: lottoNumberList,
    lottoNumberSaveList: lottoNumberSaveList,
    lottoFooter: lottoFooter
  },
  methods: {
    makeLottoNumber() {
      const MaxNumber = 45;
      var numberList=[];
      for(var i=0; i<MaxNumber; i++){
        numberList.push(i+1);
      }
      var lottolength = MaxNumber;

      // shuffle
      numberList =  this.shuffle(numberList,lottolength);
      // get 6 Numbers
      this.lottoNumbers = numberList.slice(0,6);
      console.log(this.lottoNumbers);
  	},
    saveLottoNumber(){
      // 버튼이 눌리면 savebutton이 나오기 때문에
      // validation 필요가 없음
        this.index++;
        // var STORAGE_KEY = 'Get Lotto Number version.1'
        var lotto_number = this.lottoNumbers;
        var templottoNumbers ={}
        templottoNumbers.numbers = lotto_number;
        templottoNumbers.index = this.index;

        this.savedNumbers.push(templottoNumbers);
        localStorage.setItem(this.index, JSON.stringify(templottoNumbers))
        //로컬스토리지 덮어 쓴다.

    },
    shuffle(items,n){
      while (n--) {
        var i = Math.floor(n * Math.random());
        var tmp = items[i];
        items[i] = items[n];
        items[n] = tmp;
      }
      return items;
      // https://jsperf.com/array-shuffle-comparator/5
    },
    deleteLottoNumbers(item,index){
      console.log('하이:',item,index);
      console.log(this.savedNumbers);
      this.savedNumbers.splice(index, 1);
      localStorage.removeItem(index+1);
    },
    allCLear(){
      this.savedNumbers =[];
      localStorage.clear();
      this.index = 0;
    }
  },
  // watch: {
  //   lottoNumbers: {
  //     handler: function (lottoNumber) {
  //       console.log("changed");
  //     }
  //   }
  // },
    watch: {
     savedNumbers: {
     handler: function (lottoNumber) {
         console.log("changed");
       }
    }
   }
}


</script>

<style lang="sass">
*
  box-sizing: border-box
html
  font-family: 'Roboto', sans-serif
  font-size: 16px
body
  min-height: 100vh
  background-color: #f59735
  position: relative
ul
  padding: 0
li
  list-style: none

body,h1,ul
  margin: 0

</style>
