<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <h4>{{ products[selectedIdx].title }}</h4>
      <img :src="products[selectedIdx].image" />
      <p>{{ products[selectedIdx].content }}</p>
      <button @click="showModal = false">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="menu in menuList" :key="menu">{{ menu }}</a>
  </div>

  <DiscountBanner />

  <div v-for="(product, i) in products" :key="i" @click="setShowModal(i)">
    <img :src="product.image" class="image" @click="showModal = true" />
    <h4>{{ product.title }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고수: {{ product.report }}</span>
  </div>
</template>

<script>
import DiscountBanner from "./components/DiscountBanner.vue";
import room from "./data/room.js";

export default {
  name: "App",
  data() {
    return {
      products: room,
      showModal: false,
      selectedIdx: 0,
    };
  },
  methods: {
    increase(i) {
      this.products[i].report++;
    },
    setShowModal(i) {
      this.selectedIdx = i;
      this.showModal = true;
    },
  },
  components: { DiscountBanner },
};
</script>

<style>
body {
  text-align: center;
  margin: 0;
}
div {
  box-sizing: border-box;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  cursor: pointer;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 10px;
}

.image {
  width: 350px;
  height: auto;
  margin-top: 20px;
}
.black-bg {
  width: 100vw;
  height: 100vw;
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
</style>
