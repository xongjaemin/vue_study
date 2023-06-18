<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <h4>{{ products[selectedIdx].title }}</h4>
      <img :src="products[selectedIdx].image" />
      <p>{{ products[selectedIdx].content }}</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailModal",
  props: {
    products: Array,
    selectedIdx: Number,
    showModal: Boolean,
  },
};
</script>

<style></style>
