<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <h4>{{ products[selectedIdx].title }}</h4>
      <img :src="products[selectedIdx].image" class="productImage" />
      <p>{{ products[selectedIdx].content }}</p>
      <input @input="setMonth($event.target.value)" />
      <p>{{ products[selectedIdx].price / month }} 원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailModal",
  data() {
    return {
      month: 1,
    };
  },
  methods: {
    setMonth(inputMonth) {
      if (inputMonth != "" && inputMonth != 0) {
        this.month = inputMonth;
      }
    },
  },
  watch: {
    month(a) {
      if (typeof a === "string") {
        alert("문자열 안됨");
        this.month = 1;
      }
    },
  },
  props: {
    products: Array,
    selectedIdx: Number,
    showModal: Boolean,
  },
};
</script>

<style>
.productImage {
  width: 50%;
  height: auto;
}
</style>
