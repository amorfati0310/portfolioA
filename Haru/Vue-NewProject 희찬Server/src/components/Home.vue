<template>
  <div class="container">



    <div class="main__header-scroll">
      <img class="main__header-scroll-img" src="../images/14.jordan-whitt-54480.jpg" alt="">
      <img @click="PageDown" class="main__header-scroll-arrow vertical-active" src="../images/arrow.svg" alt="아래로 이동하시오">
      <h1 class="main__header-scroll-main"> 나는 평생 하루도 일을 하지 않았다.<br>그것은 모두 재미있는 놀이였다. <br><br>-토마스 A. 에디슨 </h1>
    </div>

    <header class="main__header">
      <h1 class="main__header-logo"><img class="main__header-logo-img" src="../images/HaruLogo_Black_Finalized.svg" alt="하루한장"><span class="main__header-logo-text">haru</span></h1>
      <nav class="main__header-nav">
        <ul class="main__header-years">
          <li class="main__header-years-heading split-line-fill">년도별</li>
          <li class="main__header-years-list"><a href="#">2017</a></li>
          <li class="main__header-years-list"><a href="#">2016</a></li>
          <li class="main__header-years-list"><a href="#">2015</a></li>
        </ul>
        <ul class="main__header-emotions">
          <li class="main__header-emotions-heading split-line-fill">감정별</li>
          <li class="main__header-emotions-happy"><a href="#">기쁨</a></li>
          <li class="main__header-emotions-sad"><a href="#">슬픔</a></li>
          <li class="main__header-emotions-anger"><a href="#">버럭</a></li>
          <li class="main__header-emotions-fear"><a href="#">쏘쏘</a></li>
          <li class="main__header-emotions-disgust"><a href="#">짜증</a></li>
        </ul>
        <a href="#" class="main__header-logout split-line-fill" Methods="POST" @click.prevent="logout">Log out</a>
    </nav>
    </header>


  <main class="main">
    <div class="main__title">
      <h2 class="main__title-main">오늘 살아있는 삶을 살아라.</h2>
      <p class="main__title-sub">소중한 <span>당신. </span> 소중한 <span>하루.</span></p>
    </div>
    <router-link to="/Edit" tag="button" class="main__button-edit" type="button" aria-label="edit">
      <img class="main__contents-button-load-img" src="../images/Pencil.svg" alt="글작성">
      <span class="main__contents-button-load-text">write</span>
    </router-link>
    <ul class="main__contents">

      <li v-for="data in posts" class="main__contents-item">
        <a @click.prevent="Detail(data.id)" class="main__contents-link" href="#">
          <img class="main__contents-item-img NewOnes" :src=data.image alt="Some image" />
          <p class="postID">{{data.id}}</p>
          <h3 class="main__contents-item-title"> {{ data.title }} </h3>
        </a>
      </li>

    </ul>

  <button @click.prevent="MorePage" class="main__contents-button-load" aria-label="Load more images" type="button">
    <svg width="40px" height="45px" viewBox="0 0 220 243" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:sketch="http://www.bohemiancoding.com/sketch/ns">
        Generator: Sketch 3.5.2 (25235) - http://www.bohemiancoding.com/sketch

        <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" sketch:type="MSPage">
            <g id="polaroid" sketch:type="MSLayerGroup">
                <rect id="Rectangle-1" fill="#979797" sketch:type="MSShapeGroup" x="0" y="0" width="220" height="243" rx="5"></rect>
                <rect id="Rectangle-2" fill="#e9ecef" sketch:type="MSShapeGroup" x="16" y="20" width="189" height="149"></rect>
                <g id="Group" transform="translate(44.000000, 77.000000)" stroke="#979797" fill="#979797" sketch:type="MSShapeGroup">
                    <circle id="Oval-1" cx="17.5" cy="17.5" r="17.5"></circle>
                    <circle id="Oval-1-Copy" cx="66.5" cy="17.5" r="17.5"></circle>
                    <circle id="Oval-1-Copy-2" cx="115.5" cy="17.5" r="17.5"></circle>
                </g>
            </g>
        </g>
    </svg>
    <span class="main__contents-button-load-text">Load more</span>
  </button>

  </main>

  <footer class="main__footer">

      <ul class="main__footer-haru">
        <li class="main__footer-haru-info"><a href>하루한장 정보</a></li>
        <li class="main__footer-haru-support"><a href="#">지원</a></li>
        <li class="main__footer-haru-blog"><a href="#">블로그</a></li>
        <li class="main__footer-haru-news"><a href="#">관련기사</a></li>
        <li class="main__footer-haru-api"><a href="#">API</a></li>
        <li class="main__footer-haru-recruit"><a href="#">채용 정보</a></li>
        <li class="main__footer-haru-privacy-info"><a href="#">개인정보처리방침</a></li>
        <li class="main__footer-haru-provision"><a href="#">약관</a></li>
        <li class="main__footer-haru-dir"><a href="#">디렉터리</a></li>
        <li class="main__footer-haru-lang"><a href="#">언어</a></li>
      </ul>

    <span class="main__footer-haru-copyright">&copy; 2017 하루한장</span>
  </footer>
  </div>

  </div>
</template>

<script>

export default {
  data() {
    return {
      posts: [],
      next: null,
      datalist: [],
      imgURL: this.$store.imgURL
    }
  },

methods: {
  Detail(id) {
    var _this= this;
    _this.$store.postID = id;
    console.log('포스트 아이디 값',this.$store.postID);

    axios.get("/post/"+this.$store.postID+"/",{
      headers: {
        'Authorization': 'Token ' + this.$store.token
      }
    })
  .then(function (response) {
    console.log(response);
    _this.$store.detailData = response.data;
    console.log("잘 들어갔나 디테일에 뿌려줄 데이터", _this.$store.detailData);

  })
    this.$router.push({path: '/Detail'})
  },
PageDown() {
  $('.main__header-scroll').addClass('nav-up');
  $('.container').addClass('remove-padding');
},
MorePage: function() {
  axios.get(this.next)
        .then(result => {
          //Add data to posts
          let performList = result.data.results;
          for(var i=0; i < performList.lenth; i++) {
            this.posts.push(performList[i]);
          }
          this.next = result.data.next;

        })
        .catch( e => {
          this.errors.push(e)
        })
},
logout() {
  axios.post('/logout/','', {
    headers: {
      'Authorization': 'Token ' + this.$store.token
    }
  })
.then(function (response) {

})


this.$router.push({path: '/login'});

}},
mounted: function mounted() {
  //do something after mounting vue instance
  console.log('mounted : ', this.$store.haruinfo);
  console.log('mounted : ', this.posts);
},
created: function created() {
  //do something after creating vue instance
  console.log('created : ', this.$store.haruinfo);
  console.log('created : ', this.posts);
},
updated: function updated() {
  //do something after updating vue instance
  console.log('updated : ', this.$store.haruinfo);
  console.log('updated : ', this.posts);
},
beforeCreate() {
  var _this=  this;
    _this.$store.token = localStorage.getItem('token');
    _this.$store.token = getCookie('HaruToken');
  //  console.log('토큰 갑 가져오나?.?',_this.$store.token);

  var token = 'Token ' + _this.$store.token;

  // console.log(token);


  console.log(axios);

   $(window).on('scroll', () => {
      if( $(window).scrollTop() > 0.2) {
       $('.main__header-scroll').addClass('nav-up');
       $('.container').addClass('remove-padding');
     }
   });

   axios.get('/user/', {
    //  headers: {
    //    'Authorization': token
    //  }
   })
 .then(function (response) {
   console.log('응답:',response.data.results[0].id);
   _this.$store.userID = response.data.results[0].id;
   console.log('스토어에 아이디 값 저장하기!!!!!',_this.$store.userID)

   axios.get('/post/', {
    //  headers: {
    //    'Authorization': 'Token ' + this.$store.token
    //  }
   })
  .then(function (response) {
    // console.log("요거는 요거는 데이터 서버에서 온 데이터", response);
    console.log('post response : ', response);
    _this.$store.haruinfo = response.data.results;
    _this.posts = response.data.results;
    _this.$data.temp = response.data.results;
    // console.log('_this.$store:',  _this.$store);
    // console.log("첫 번째 데이터 ",_this.$store.haruinfo);
  })
 });



}
}

</script>
<style lang="sass" scoped>
  @import "../Sass_main/main__page-style.sass"
</style>
