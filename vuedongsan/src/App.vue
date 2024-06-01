<!-- template 안에는 html을 짜고
script 안에는 JS 짜고
style 안에는 CSS를 짠다 -->
<template>
  <div class="menu">
    <!--
    <a>Home</a>
    <a>about</a>
    <a>products</a> -->

    <!-- 반복적인 HTML태그 축약 가능 : 반복문 사용 -->
    <!-- <태그 v-for="작명 in 횟수(혹은 배열/객체)" :key="작명">
       : 태그를 (횟수나 배열/객체의 데이터 만큼) 반복해서 작성
       : ':key'는 반드시 기입, 반복문 돌린 요소를 컴퓨터가 구분한다  -->
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <div v-for="(a, i) in products" :key="i">
    <!-- <h4>{{ products[i] }}</h4> -->
    <h4>{{ a }}</h4>
    <p>{{ prices[i] }} 만원</p>
  </div>

  <!-- 바뀌지 않는 데이터들은 바인딩할 필요가 없다 -->
  <!-- <h4>ㅇㅇ 원룸</h4> -->
  <!-- 객체로 데이터 연결 -->
  <!-- <h4>{{ menus[0] }}</h4> -->
  <!-- {{ 콧수염 안에 데이터 이름을 기입}}
           밑에 있는 데이터가 연결됨  -->
  <!-- <p>{{ price }} 만원</p>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>0000 만원</p>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>0000 만원</p>
  </div> -->
</template>

<script>
// 데이터 바인딩 : JS데이터를 HTML에 꽂아넣는 문법
// 기존 JS : document.getElementById().innerHTML = ??
// Vue : 데이터를 data() {return _{여기에 데이터 보관}}안에 넣는다

export default {
  name: 'App',
  // data 안의 내용이 변경되면 관련된 HTML에도 자동으로 렌더링됨
  data() {
    return {
      // 데이터는 object 자료로 저장한다 (작명 : 저장할 값)
      menus: ['Home', 'products', 'menu'],
      prices: ['60만원', '70만원', '80만원'],
      products: ['건대 앞 원룸', '세종대 앞 원룸', '한양대 앞 원룸'],
    };
  },
  components: {},
};
</script>

<style>
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
