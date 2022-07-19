<template>
  <div v-for="(a, i) in rooms" :key="i.id">
    <img :src="rooms[i].image" />
    <h4 @click="onClick(i)">
      {{ rooms[i].title }}
    </h4>
    <p>{{ rooms[i].price }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    rooms: Array,
  },
  methods: {
    onClick(i) {
      this.$emit("openModal", i);
    },
  },
};
</script>

<style></style>
