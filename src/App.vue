<template>
  <div class="black-bg" v-if="showModal" @click="showModal = false">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>
  <div class="menu">
    <a v-for="menu in menuList" :key="menu">{{ menu }}</a>
  </div>

  <div>
    <img src="./assets/jamie.png" class="image" @click="showModal = true" />
  </div>
  <div v-for="(product, i) in products" :key="i">
    <h4>{{ product }}</h4>
    <p>{{ price[i] }} 만원</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고수: {{ report[i] }}</span>
  </div>
</template>

<script>
import room from "./data/room.js";
room;

export default {
  name: "App",
  data() {
    return {
      price: [60, 30, 20],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      menuList: ["Home", "Products", "ETC"],
      report: [0, 0, 0],
      showModal: false,
    };
  },
  methods: {
    increase(i) {
      this.report[i]++;
    },
  },
  components: {},
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
