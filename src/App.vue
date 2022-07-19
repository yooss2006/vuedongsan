<template>
  <!-- <div v-if="1 == 2">하이</div>
  <div v-else-if="1 == 1">하하</div>
  <div v-else>놉</div> -->

  <transition name="fade">
    <Modal
      :isModal="isModal"
      :rooms="rooms"
      :clickNumber="clickNumber"
      @closeModal="isModal = false"
    />
  </transition>
  <div class="menu">
    <a v-for="(a, index) in menus" :key="index">{{ a }}</a>
  </div>
  <Discount v-if="showDiscount === true" />

  <button @click="priceSort">가격순 정렬</button>
  <button @click="priceReverseSort">가격 역순 정렬</button>
  <button @click="priceTitleSort">가나다 정렬</button>
  <button @click="sortBack">되돌리기</button>
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
      showDiscount: true,
      clickNumber: 0,
      originalRooms: [...data],
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
    priceSort() {
      this.rooms.sort((a, b) => {
        return a.price - b.price;
      });
    },
    priceReverseSort() {
      this.rooms.sort((a, b) => {
        return b.price - a.price;
      });
    },
    priceTitleSort() {
      this.rooms.sort((a, b) => {
        if (a.title < b.title) return -1;
        if (a.title > b.title) return 1;
        if (a.title === b.title) return 0;
        else return -1;
      });
    },
    sortBack() {
      this.rooms = [...this.originalRooms];
    },
  },
  // mounted() {
  //   setTimeout(() => {
  //     this.showDiscount = false;
  //   }, 2000);
  // },

  //서버에서 데이터 가져올 때
  created() {},

  components: {
    Discount,
    Modal,
    Card,
  },
};
</script>

<style>
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

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
