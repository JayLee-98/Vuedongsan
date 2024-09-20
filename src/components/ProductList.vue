<template>
  <div>
    <h2>원룸 목록</h2>
    <div class="studio-grid">
      <div v-for="studio in studios" :key="studio.id" class="studio-card">
        <img :src="studio.image" :alt="studio.title" class="studio-img" />
        <h3>{{ studio.title }}</h3>
        <p>{{ studio.price.toLocaleString() }}원</p>
        <button @click="$emit('open-modal', studio)">상세 정보</button>
      </div>
    </div>
  </div>
</template>

<script>
import studios from '../assets/oneroom.js';

export default {
  name: 'ProductList',
  data() {
    return {
      studios: studios
    }
  }
}
</script>

<style scoped>
.studio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 2rem;
}

.studio-card {
  background-color: var(--accent-color);
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  transition: transform 0.3s;
  color: var(--text-color);
}

.studio-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 6px rgba(0,237,100,0.1);
}

.studio-img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 5px;
  margin-bottom: 1rem;
}

h3 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  color: var(--main-color);
}
</style>