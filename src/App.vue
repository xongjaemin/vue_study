<template>
  <!-- 상세조회 모달 -->
  <DetailModal
    :products="products"
    :selectedIdx="selectedIdx"
    :showModal="showModal"
    @closeModal="showModal = false"
  />
  <div class="menu">
    <a v-for="menu in menuList" :key="menu">{{ menu }}</a>
  </div>

  <DiscountBanner v-if="showDiscount" :discount="discount" />

  <!-- 상품 리스트 -->
  <ProductList
    v-for="(product, i) in products"
    :key="i"
    @setShowModal="setShowModal($event)"
    @increaseReport="increase(i)"
    :product="product"
  />
</template>

<script>
import DiscountBanner from "./components/DiscountBanner.vue";
import DetailModal from "./components/DetailModal.vue";
import ProductList from "./components/ProductList.vue";
import room from "./data/room.js";

export default {
  name: "App",
  data() {
    return {
      products: room,
      showModal: false,
      selectedIdx: 0,
      discount: 30,
      showDiscount: true,
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

  mounted() {
    setInterval(() => {
      this.discount -= 1;
    }, 1000);
  },

  components: { DiscountBanner, DetailModal, ProductList },
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
