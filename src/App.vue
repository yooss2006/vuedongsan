<template>
  <div class="black-bg" v-if="isModal" @click="isModal = false">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
    </div>
  </div>
  <div class="menu">
    <a v-for="(a, index) in menus" :key="index">{{ a }}</a>
  </div>
  <div v-for="(a, i) in products.length" :key="i">
    <img src="./assets/room1.jpg" />
    <h4 @click="isModal = true">{{ products[i] }}</h4>
    <p>50 만원</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고 수 : {{ number[i] }}</span>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      isModal: false,
      number: [0, 0, 0],
      menus: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase(i) {
      this.number[i] += 1;
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
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
