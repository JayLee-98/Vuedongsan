<template>
  <div class="modal" v-if="selectedStudio">
    <div class="modal-content">
      <h4>{{ selectedStudio.title }}</h4>
      <img :src="selectedStudio.image" class="room-img" />
      <p>{{ selectedStudio.content }}</p>
      <p>{{ selectedStudio.price }}원</p>
      <button @click="selectedStudio = null">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div v-for="(a, i) in studios" :key="i">
    <img :src="a.image" class="room-img" />
    <h4 @click="openModal(a)" style="cursor: pointer">{{ a.title }}</h4>
    <p>{{ a.price }}원</p>
  </div>
</template>

<script>
import studios from "./assets/oneroom.js";

export default {
  name: "App",
  data() {
    return {
      studios: studios,
      selectedStudio: null,
      menus: ["Home", "Products", "About"],
    };
  },
  methods: {
    openModal(studio) {
      this.selectedStudio = studio;
    },
  },
  watch: {
    selectedStudio(newValue) {
      if (newValue) {
        document.body.style.overflow = 'hidden';
      } else {
        document.body.style.overflow = '';
      }
    }
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

.modal {
  position: fixed;
  z-index: 9999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.4);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  background-color: #fefefe;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
  max-width: 600px;
  max-height: 80vh;
  overflow-y: auto;
  border-radius: 5px;
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
