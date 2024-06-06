<!-- template 안에는 html을 짜고
  script 안에는 JS 짜고
  style 안에는 CSS를 짠다 -->
<template>
  <!-- v-if="조건식" : 조건식이 참일때만 HTML을 보여줌 -->
  <div class="black-bg" v-if="modalStatus == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세 페이지 내용</p>
      <button @click="modalStatus = false">닫기</button>
    </div>
  </div>
  <div class="menu">
    <!--
        <a>Home</a>
        <a>about</a>
        <a>products</a> -->

    <!-- 바뀌지 않는 데이터들은 바인딩할 필요가 없다 -->
    <!-- <h4>ㅇㅇ 원룸</h4> -->
    <!-- 객체로 데이터 연결 -->
    <!-- <h4>{{ menus[0] }}</h4> -->

    <!-- 반복적인 HTML태그 축약 가능 : 반복문 사용 -->
    <!-- <태그 v-for="작명 in 횟수(혹은 배열/객체)" :key="작명">
          : 태그를 (횟수나 배열/객체의 데이터 만큼) 반복해서 작성
          : ':key'는 반드시 기입, 반복문 돌린 요소를 컴퓨터가 구분한다  -->
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <!-- <div v-for="(a, i) in products" :key="i"> -->
  <!-- <h4>{{ products[i] }}</h4> -->
  <!-- <h4>{{ a }}</h4> -->
  <!-- <p>{{ prices[i] }} 만원</p> -->
  <!-- </div> -->

  <!-- {{ 콧수염 안에 데이터 이름을 기입}}
           밑에 있는 데이터가 연결됨  -->
  <div>
    <!-- 이미지 넣는 법 : <img src="이미지경로"> -->
    <!-- <img
      src="https://cdn.ggumim.co.kr/cache/star/600/20190103195414wob5asyPJA.jpg"
      class="room-img"
    /> -->
    <img :src="onerooms[0].image" class="room-img" />
    <!-- 상품명 클릭 시 모달창상태를 true로 변경 -->
    <h4 @click="modalStatus = true">{{ onerooms[0].title }}</h4>
    <p>{{ onerooms[0].price }} 원</p>

    <!-- for문으로 구현해보자!! -->

    <!-- 버튼 클릭 시 자바스크립트 실행하려면 onClick="" -->
    <!-- vue 방식은 v-on:이벤트="" , v-on:은 @로 축약 가능 -->
    <!-- reportCount++ : reportCount 값을 1개 더해줌
         (reportCount += 1 혹은 reportCount = reportCount+1 과 같다) -->
    <!-- <button @click="reportCount++">허위매물 신고</button> -->

    <!-- 이벤트에 자바스크립트의 함수를 연결 가능함. 함수명만 기입 -->
    <button @click="reportCount[0]++">허위매물 신고</button>
    <span> 신고 수 : {{ reportCount[0] }}</span>
  </div>
  <div>
    <img
      src="https://i.pinimg.com/736x/4c/ea/83/4cea835a5ea72c48ec13fe74a740489a.jpg"
      class="room-img"
    />
    <h4>{{ products[1] }}</h4>
    <p>{{ prices[1] }} 만원</p>
    <button @click="reportCount[1]++">허위매물 신고</button>
    <span> 신고 수 : {{ reportCount[1] }}</span>
  </div>
  <div>
    <img
      src="https://image.ohou.se/i/bucketplace-v2-development/uploads/cards/snapshots/170718700510328129.jpeg?gif=1&w=480&h=480&c=c&q=80"
      class="room-img"
    />
    <h4>{{ products[2] }}</h4>
    <p>{{ prices[2] }} 만원</p>
    <button @click="reportCount[2]++">허위매물 신고</button>
    <span> 신고 수 : {{ reportCount[2] }}</span>
  </div>
</template>

<script>
// 데이터 바인딩 : JS데이터를 HTML에 꽂아넣는 문법
// 기존 JS : document.getElementById().innerHTML = ??
// Vue : 데이터를 data() {return _{여기에 데이터 보관}}안에 넣는다
import data from './assets/oneroom.js';
export default {
  name: 'App',
  // data 안의 내용이 변경되면 관련된 HTML에도 자동으로 렌더링됨
  data() {
    return {
      // 데이터는 object 자료로 저장한다 (작명 : 저장할 값)
      onerooms: data,
      menus: ['Home', 'products', 'menu'],
      prices: ['60만원', '70만원', '80만원'],
      products: ['건대 앞 원룸', '세종대 앞 원룸', '한양대 앞 원룸'],
      reportCount: [0, 0, 0],
      // ui 현재 상태를 데이터로 저장해둠 (0:닫힘, 1: 열림)
      modalStatus: 0,
    };
  },
  // vue에서 함수 만들고 싶을때는 data 뒤에 methods:{}를 만든다
  methods: {
    increase() {
      this.reportCount += 1;
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
