<template>
  <header>
    <nav>
      <ul class="menu">
        <li v-for="(item, index) in menuItems" :key="index">
          <a @click="currentPage = item.component">{{ item.name }}</a>
        </li>
      </ul>
    </nav>
  </header>

  <main>
    <component :is="currentPage" @open-modal="openModal"></component>
  </main>

  <div class="modal" v-if="selectedStudio">
    <div class="modal-content">
      <h4>{{ selectedStudio.title }}</h4>
      <img :src="selectedStudio.image" class="room-img" alt="Studio Image" />
      <p>{{ selectedStudio.content }}</p>
      <p><strong>가격:</strong> {{ selectedStudio.price.toLocaleString() }}원</p>
      <button @click="closeModal">닫기</button>
    </div>
  </div>
</template>

<script>
import Home from './components/HomePage.vue';
import Products from './components/ProductList.vue';
import About from './components/AboutPage.vue';

export default {
  name: "App",
  components: {
    Home,
    Products,
    About
  },
  data() {
    return {
      selectedStudio: null,
      currentPage: Home,
      menuItems: [
        { name: 'Home', component: Home },
        { name: 'Products', component: Products },
        { name: 'About', component: About },
      ],
    };
  },
  methods: {
    openModal(studio) {
      this.selectedStudio = studio;
    },
    closeModal() {
      this.selectedStudio = null;
    }
  },
  watch: {
    selectedStudio(newValue) {
      document.body.style.overflow = newValue ? 'hidden' : '';
    }
  },
};
</script>

<style>
:root {
  --main-color: #00ed64; /* Hulu 초록색 */
  --accent-color: #000000; /* 검정색 */
  --text-color: #ffffff; /* 흰색 */
  --background-color: #121212; /* 매우 어두운 회색 */
}

body {
  font-family: 'Arial', sans-serif;
  background-color: var(--background-color);
  color: var(--text-color);
  margin: 0;
  padding: 0;
}

#app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

header {
  background-color: var(--accent-color);
  padding: 1rem;
  border-radius: 10px;
  margin-bottom: 20px;
}

.menu {
  list-style-type: none;
  padding: 0;
  margin: 0;
  display: flex;
  justify-content: center;
}

.menu li {
  margin: 0 1rem;
}

.menu a {
  color: var(--main-color);
  text-decoration: none;
  cursor: pointer;
  font-weight: bold;
}

.menu a:hover {
  color: var(--text-color);
}

main {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.modal {
  position: fixed;
  z-index: 9999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.8);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  background-color: var(--accent-color);
  color: var(--text-color);
  padding: 2rem;
  border-radius: 10px;
  width: 80%;
  max-width: 600px;
  max-height: 80vh;
  overflow-y: auto;
  box-shadow: 0 4px 6px rgba(0,237,100,0.1);
}

.room-img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 5px;
  margin-bottom: 1rem;
}

button {
  background-color: var(--main-color);
  border: none;
  color: var(--accent-color);
  padding: 0.5rem 1rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.3s, color 0.3s;
}

button:hover {
  background-color: var(--accent-color);
  color: var(--main-color);
  border: 1px solid var(--main-color);
}
</style>
