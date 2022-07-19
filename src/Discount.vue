<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discount }}%할인</h4>
  </div>
</template>

<script>
export default {
  name: "Discount",
  data() {
    return {
      discount: 30,
    };
  },
  mounted() {
    console.log(this.discount);
    let interval = setInterval(() => {
      this.discount = this.discount - 1;
      if (this.discount <= 0) {
        clearInterval(interval);
      }
    }, 1000);
  },
};
</script>

<style>
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
