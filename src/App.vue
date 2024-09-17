<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div class="black-bg" v-if="isModalOpen == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="isModalOpen = false">닫기</button>

    </div>
  </div>

  <div>
    <!-- <div v-for="product in products" :key="product"> -->
    <!-- <h4>{{ product }}</h4> -->
    <img src="./assets/room0.jpg" class="room-img" />
    <h4 @click="isModalOpen = true">{{ products[0] }}</h4>
    <p>50 만원</p>
    <button @click="reports[0]++">허위매물신고</button>
    <span>신고 수: {{ reports[0] }}</span>
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img" />
    <h4 @click="isModalOpen = true">{{ products[1] }}</h4>
    <p>60 만원</p>
    <button @click="reports[1]++">허위매물신고</button>
    <span>신고 수: {{ reports[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img" />
    <h4 @click="isModalOpen = true"> {{ products[2] }}</h4>
    <p>70 만원</p>
    <button @click="reports[2]++">허위매물신고</button>
    <span>신고 수: {{ reports[2] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      isModalOpen : false,
      reports: [0, 0, 0],
      menus: ["Home", "Products", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase() {
      this.reports++;
    },
  },
  components: {},
};
</script>

<style>
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

.room-img {
  width: 100%;
  margin-top: 40px;
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

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
