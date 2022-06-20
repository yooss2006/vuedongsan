<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div>
    <h4>{{ products[0] }}</h4>
    <p>50 만원</p>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>50 만원</p>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>50 만원</p>
  </div>
</template>
<script>
// vue의 실시간 자동 렌더링 기능을 사용하고 싶으면 {{}}를 사용해라.
// data를 변경함녀 data와 관련된 HTML도 실시간으로 반영된다.

export default {
  name: "App",
  data() {
    return {
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
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
