<template>
  <div class="container">

    <div class="main__header-scroll">
      <img class="main__header-scroll-img" src="../images/14.jordan-whitt-54480.jpg" alt="">
      <img @click="PageDown" class="main__header-scroll-arrow vertical-active" src="../images/arrow.svg" alt="아래로 이동하시오">
      <h1 class="main__header-scroll-main"> 매일 매일이 일년중에 최고의 날임을 <br> 가슴속에 새겨두어라 . </h1>
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




      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/1.andreas-p-30199.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">Castle in the twilight</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/2.chuttersnap-193788.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">Natural saturation effects</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/3.darius-soodmand-116253.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">Tip of iceberg</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/4.miguel-mateo-212333.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">Run on the hill</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/6.alejandra-quiroz-658.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">A tired day</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/7.averie-woodard-111822.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">A tired day</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/10.gabor-juhasz-68424.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">Into the forest</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/12.jonatan-pie-234237.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">It's so beautiful.</h3>
        </a>
      </li>
      <li class="main__contents-item">
        <a class="main__contents-link" href="#">
          <img class="main__contents-item-img" src="../images/19.samuel-zeller-157390.jpg" alt="Some image" />
          <h3 class="main__contents-item-title">Early adopters</h3>
        </a>
      </li>

      <li v-for="data in datalist" class="main__contents-item" @click="gotoDeatil">
        <a class="main__contents-link" href="#">
          <img  class="main__contents-item-img newOnes" alt="Some image" />
          <!-- v-attr="src ={{data.image}}" -->
          <h3 class="main__contents-item-title"> {{ data.title }}</h3>
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
// import {EventBus} from '../../event-bus.js'
export default {
  data() {
    return {
      posts: [],
      next: null,
      datalist: [],
      imgURL: this.$store.imgURL,
      imgUrlList:[]
    }
  },

methods: {
PageDown() {
  $('.main__header-scroll').addClass('nav-up');
  $('.container').addClass('remove-padding');
},
gotoDeatil(){
    this.$router.push('/Detail')
}
,
logout() {
  console.log('logout token: ', this.$store.token)
  axios.post('/logout/','', {
    headers: {
      'Authorization': 'Token ' + this.$store.token
    }
  })
.then(function (response) {
  console.log('응답:',response);
})
this.$router.push({path: '/login'});
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
}

},

mounted() {




           $(window).on('scroll', () => {

              if( $(window).scrollTop() > 0.2) {
               $('.main__header-scroll').addClass('nav-up');
               $('.container').addClass('remove-padding');
             }
           });
       },
created() {
            console.log('이미지 url',this.$store.imgURL);

  this.$http.get('https://haruphoto-6ad66.firebaseio.com/haru_diary.json')
            .then(function(response) {
              return response.json();
            })
            .then( function(data) {
              this.datalist = Object.values(data);
            })
            .catch(function(error) {
              console.error(error.message)
            });




},
updated: function updated() {


  axios.get('/user/', {
    headers: {
      'Authorization': 'Token ' + this.$store.token
    }
  })
.then(function (response) {
  console.log('응답:',response);
})

  // var i=0;
  // console.log("데이타에 이미지 링크  확인 ",this.datalist[i].image);

  var newHaru = document.querySelectorAll('.newOnes')
  console.log('newHaru :', newHaru)
  var length = newHaru.length;
  //
  for(var i= 0; i<length; i++ ){
    newHaru[i].setAttribute('src',this.datalist[i].image )
  }




 // // console.log(ImgSrc[ImgSrc.length - 1].setAttribute.src = this.imgURL),
 // ImgSrc[ImgSrc.length - 1].setAttribute('src', this.imgURL)
 //   console.log('this.imgURL___지금 :', this.imgURL)

}

}

</script>
<style lang="sass" scoped>
  @import "../Sass_main/main__page-style.sass"
</style>
