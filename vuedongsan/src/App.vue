<!-- template 안에는 html을 짜고
script 안에는 JS 짜고
style 안에는 CSS를 짠다 -->
<template>
  <div>
    <!-- 바뀌지 않는 데이터들은 바인딩할 필요가 없다 -->
    <!-- <h4>ㅇㅇ 원룸</h4> -->
    <h4>{{ menus[0] }}</h4>
    <!-- {{ 콧수염 안에 데이터 이름을 기입}}
           밑에 있는 데이터가 연결됨  -->
    <p>{{ price1 }} 만원</p>
  </div>
  <div>
    <h4>{{ menus[1] }}</h4>
    <p>0000 만원</p>
  </div>
  <div>
    <h4>{{ menus[2] }}</h4>
    <p>0000 만원</p>
  </div>
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
      price1: 60,
      price2: 70,
      price3: 80,
      menus: ['건대 앞 원룸', '세종대 앞 원룸', '한양대 앞 원룸'],
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
</style>
