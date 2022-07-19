<template>
  <!-- <div v-if="1 == 2">하이</div>
  <div v-else-if="1 == 1">하하</div>
  <div v-else>놉</div> -->

  <Modal
    :isModal="isModal"
    :rooms="rooms"
    :clickNumber="clickNumber"
    @closeModal="isModal = false"
  />
  <div class="menu">
    <a v-for="(a, index) in menus" :key="index">{{ a }}</a>
  </div>
  <div v-if="isModal"></div>
  <Discount />
  <Card
    :rooms="rooms"
    @openModal="
      isModal = true;
      clickNumber = $event;
    "
  />
</template>
<script>
import data from "./assets/data";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      clickNumber: 0,
      rooms: data,
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
    handleIsModal() {
      this.isModal = this.isModal ? false : true;
    },
    titleClick(num) {
      this.isModal = true;
      this.clickNumber = num;
    },
  },
  components: {
    Discount,
    Modal,
    Card,
  },
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
