# get_lottery_number

가끔 로또를 하는데 맨날 안 맞아서... 조금 확률 높은 복권 번호 추첨해 주는 사이트를 직접 만들어보자 :D

1차 뭐가 있을까
Random으로 뽑아주는데

어떤 조건을 걸어야 할까?

한 10회차쯤 자료를 보고 분석해보자

1,3,12,21,26,41
4,7,11,24,42,45
10,22,27,31,42,43
9,33,36,40,42,43
5,9,12,30,39,43
6,7,11,17,33,44
10,14,16,18,27,28
13,14,26,28,30,36
2,8,17,24,28,29
2,17,19,24,37,41


+ 의외로 연속 된 숫자들이나오네 신기
28,29 같이그런 것들 제외하려고 했는데
+ 자리수 개념
1 2개 10 1개 20 2개 40 1개
1 2개 10 1개 20 1개 40 2개
10 1개 20 2개 30 1개 40 2개
or
자리수 갯수는 1,1,2,2가 제일 많고
그 다음 1,2,3
2,2,2
3,3이나 자릿수에서 4개가 나오면 제외하는 형식으로

+ 직전 숫자가또 나오는 경우는 없다고 생각했는데 이거도간혹 있네...
14,2,17..의미가 없어지나 1개 이상 나오면 바꾸는 형식으로





> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
