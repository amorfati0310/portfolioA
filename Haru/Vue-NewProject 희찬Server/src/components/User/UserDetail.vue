<template>
  <div class="wrapper">
    <!-- 모달 윈도우 -->
    <div class="modal"  v-if="ShowDetail" >
      <!-- 상세 페이지 컨텐츠 영역 -->
      <section class="detail-contents"  >
        <!-- 상세페이지 나가기 버튼 -->
        <img class="detail-contents--exit" src="../../images/x_button.png" alt="나가기 버튼" width="32" height="32" @click="goHome">
        <!-- 컨텐츠 내용 영역 -->
        <article class="detail-contents__article" >
          <figure class="detail-contents__figure">
            <!-- 컨텐츠 이미지 -->

            <img :src=this.$store.detailData.image alt="" class="detail-contents--image" width="600" height="400">

            <img src="../../images/emotions/angry.svg" alt="기쁨" class="detail-contents--emotion" width="40" height="40">
          </figure>
          <!-- <div class="untitle"> -->
            <!-- 컨텐츠 제목 영역 -->
            <h1 class="detail-contents__title">{{this.$store.detailData.title}}</h1>
            <!-- 컨텐츠 내용 영역 -->
            <p class="detail-contents__text">{{this.$store.detailData.content}} </p>
            <!-- 날짜 시간 영역 -->
            <p class="detail-content--date">
              <span class="nowtime"></span>
            </p>
            <div class="detail-contents__button--box">
              <button type="button" class="detail-contents--modify__button" @click.prevent="gotoModify">수정</button>
              <button type="button" class="detail-contents--delete__button" @click.prevent="deleteHaru">삭제</button>
            </div>
          <!-- </div> -->
        </article>
        <div class="arrow-box">
          <button type="button" class="detail-contents--arrow-left">
            <img src="../../images/arrow-left.png" alt="이전 컨텐츠 이동" width="60" height="80">
          </button>
          <button type="button" class="detail-contents--arrow-right">
            <img src="../../images/arrow-right.png" alt="다음 컨텐츠 이동" width="60" height="80">
          </button>
        </div>
      </section>

      </div>
      <div class="wrapper2" v-if="ShowModify">
        <div class="modify__box">

          <form class="modify__contentsBox" ref="form" method="POST"  enctype="multipart/form-data" @submit.prevent="ModifyHaru">
            <div  class="modify__imageBox">
              <div v-if="!image" class="imageInputbox">
                <input type="file" @change="onFileChange" class="pa haruphoto" id="haruphoto"/>
                <img src="../../images/writepage/buttons/imageIcon.svg" alt="컨텐츠 이미지" title="컨텐츠 이미지" class="imageIcon">
              </div>
              <div v-else class="prevImgBox">
                <img name="image" v-model="haru_diary.image" :src="image"  class="prevImg" >
                <button @click="removeImage" class="pa img-upload-cancel-btn">Remove image</button>
              </div>
              <progress v-show="Show" value="0" max="100" id="uploader">0%</progress>
            </div>
            <div class="modify__textBox">

              <input class="modify__haru-title" type="text" name="title" :placeholder=$store.detailData.title v-model="haru_diary.title">
              <div name="emotions" class="modify__emotions">
                <input value = 1 title="기쁨" type="radio" name="status" v-model="haru_diary.status" class="modify__emotions-happy"><img src="../../images/emotions/happy.svg" alt="기쁨" width="25" height="25">
                <input value = 2 title="그럭저럭" type="radio" name="status" v-model="haru_diary.status" class="modify__emotions-normal"><img src="../../images/emotions/normal.svg" alt="보통" width="25" height="25">
                <input value = 3 title="슬픔" type="radio" name="status" v-model="haru_diary.status" class="modify__emotions-sad"><img src="../../images/emotions/sad.svg" alt="슬픔" width="25" height="25">
                <input value = 4 title="짜증" type="radio" name="status" v-model="haru_diary.status" class="modify__emotions-rage"><img src="../../images/emotions/irritation.svg" alt="짜증" width="25" height="25">
                <input value = 5 title="분노" type="radio" name="status" v-model="haru_diary.status" class="modify__emotions-angry"><img src="../../images/emotions/angry.svg" alt="분노" width="25" height="25">
              </div>
              <textarea class="modify__haru-text" name="content" :placeholder=$store.detailData.content v-model="haru_diary.content" ></textarea>
            </div>
            <button type="submit" name="button" class="modify__button" @click.prevent="ModifyHaru" >수정하기</button>
            <span class="nowtime"></span>
          </form>
        </div>
        <button class="modal-close" @click="gotoDetail"></button>
      </div>
    </div>

  </div>

</template>
<script>
export default {
  name: "",
  data: function data() {
    return {
      ShowDetail: true,
      ShowModify: false,
      haru_diary: {
        author: this.$store.userID,
        title: this.$store.detailData.title,
        content: this.$store.detailData.content,
        status: this.$store.detailData.status,
        image: this.$store.detailData.image
      },
      haruUrl:'',
      Show: false,
      image: this.$store.detailData.image
    }
  },
  methods: {
    goHome() {
      this.$router.push('/home');
    },
    deleteHaru(){
      var _this = this;
      console.log('글 숫자 가지고 있어?',_this.$store.postID)
      // axios.post("/post/"+_this.$store.postID+"/",{
        axios.delete("/post/"+_this.$store.postID+"/",{
        // headers: {
        //   'Authorization': 'Token ' + _this.$store.token
        // }
      }).then(function(){
          _this.$router.push('/home');
      });
    },
    gotoModify(){
      this.ShowDetail = false;
      this.ShowModify = true;
      console.log('이미지 왜 못 가지고 오지?',this.$store.detailData.image);


    },
    ModifyHaru(){

      console.log("수정하기 보내기");

      var _this = this;



      _this.haru_diary.status = Number(_this.haru_diary.status )

      const edit_data = new FormData();
    edit_data.append('author', this.$store.userID);
    edit_data.append('title', _this.haru_diary.title);
    edit_data.append('content', _this.haru_diary.content);
    edit_data.append('status', _this.haru_diary.status);
    edit_data.append('image', _this.haru_diary.image);




      axios.patch("/post/"+_this.$store.postID+"/",edit_data,{

    }).then(function(response){
        console.log(response.data);
        _this.$router.push('/home');
    });

    },
    gotoDetail(){
      this.ShowDetail = true;
      this.ShowModify = false;
    },
    onFileChange(e) {
      var files = e.target.files || e.dataTransfer.files;
      if (!files.length)
        return;
      this.createImage(files[0]);
      this.haru_diary.image = e.target.files[0];
      // this.image = e.target.files[0];
      console.log( 'this.haru_diary.image :', this.haru_diary.image)
      // console.log( 'this.haru_diary.image :', this.image)
    },
    createImage(file) {
      var image = new Image();
      var reader = new FileReader();
      var vm = this;

      reader.onload = (e) => {
        vm.image = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    removeImage: function (e) {
      this.image = '';
    }
  },
  mounted() {
    //일단 날짜 표시
    var now_time = document.querySelector('.nowtime');
    var now = new Date();
    var years = now.getFullYear();
    var month = now.getMonth()+1;
    if(month<10){
      month='0'+month;
    }
    var day = now.getDate();
    var hours = now.getHours();

    now_time.innerHTML=`${years}-${month}-${day}`

    console.log("헐 이건데",this.$store.detailData);
    var detailEmotion = document.querySelector('.detail-contents--emotion');

    switch(this.$store.detailData.status) {
    case 1:
        detailEmotion.setAttribute('src',"/dist/happy.svg")
        break;
    case 2:
        detailEmotion.setAttribute('src',"/dist/normal.svg")
        break;
    case 3:
        detailEmotion.setAttribute('src',"/dist/sad.svg")
        break;
    case 4:
        detailEmotion.setAttribute('src',"/dist/irritation.svg")
        break;
    case 5:
        detailEmotion.setAttribute('src',"/dist/angry.svg")
        break;
    default:
        break;
    }
  }
}
</script>
<style lang="sass" scoped>
  @import "../../Sass_detail/main.sass"
</style>
