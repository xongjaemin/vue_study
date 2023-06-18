<template>
  <div>
    <img :src="product.image" class="image" />
    <h4 @click="$emit('setShowModal', product.id)">{{ product.title }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @click="$emit('increaseReport')">허위매물신고</button>
    <span>신고수: {{ product.report }}</span>
  </div>
</template>

<script>
export default {
  name: "ProductList",
  props: {
    product: Object,
  },
};
</script>

<style></style>
