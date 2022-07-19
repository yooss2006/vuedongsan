<template>
  <div class="black-bg" v-if="isModal == true">
    <div class="white-bg">
      <h4>{{ rooms[clickNumber].title }}</h4>
      <p>{{ rooms[clickNumber].content }}</p>
      <!-- <input @input="month = $event.target.value" /> -->
      <input v-model.number="month" />
      <p>{{ rooms[clickNumber].price * month }}</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(x) {
      if (isNaN(x) == true) {
        alert("문자 입력 ㄴㄴ");
        this.month = 1;
      }
    },
  },
  props: {
    rooms: Array,
    isModal: Boolean,
    clickNumber: Number,
  },
};
</script>

<style></style>
