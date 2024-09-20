<template>
  <div>
    <div class="home">
      <h1>원룸 찾기에 오신 것을 환영합니다</h1>
      <p>저희는 최고의 원룸 선택을 도와드립니다.</p>
      <div style="text-align: right;">
        <button @click="goToProducts">원룸 보러가기</button>
      </div>
    </div>

    <div class="bento-grid">
      <div class="card logo">
        <h2>원룸</h2>
        <p>당신의 새로운 보금자리</p>
      </div>
      <div class="card post-task">
        <button>원하는 조건 등록하기 →</button>
      </div>
      <div class="card agents">
        <div class="agent" v-for="agent in agents" :key="agent.name">
          <p>{{ agent.name }}</p>
          <p>{{ agent.role }}</p>
          <button>연락하기</button>
        </div>
      </div>
      <div class="card icons">
        <div class="icon-group">
          <span>🔍</span>
          <span>❤️</span>
          <span>🎁</span>
        </div>
        <div class="icon-group">
          <span>👤</span>
          <span>💬</span>
          <span>🏠</span>
        </div>
      </div>
      <div class="card emoji">
        <span>🏙️</span>
        <span>🏘️</span>
        <span>🌳</span>
        <span>🚗</span>
      </div>
      <div class="card price">
        <h2>₩450,000</h2>
        <p>평균 월세</p>
        <small>지역과 조건에 따라 가격이 다를 수 있습니다</small>
      </div>
      <div class="card services">
        <ul>
          <li v-for="service in services" :key="service.name">
            <span>{{ service.icon }} {{ service.name }}</span>
            <span>{{ service.count }}</span>
          </li>
        </ul>
      </div>
      <div class="card slogan">
        <h2>당신의 집에 맞는 맞춤 서비스</h2>
        <p>원룸 찾기부터 입주까지 모든 과정을 도와드립니다</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      agents: [
        { name: '김철수', role: '부동산 전문가' },
        { name: '이영희', role: '계약 상담사' },
        { name: '박지성', role: '타일 시공사' }
      ],
      services: [
        { name: '이사', icon: '🚚', count: 50 },
        { name: '청소', icon: '🧹', count: 30 },
        { name: '수리', icon: '🔧', count: 25 },
        { name: '인테리어', icon: '🎨', count: 15 }
      ]
    }
  },
  methods: {
    goToProducts() {
      this.$parent.currentPage = this.$parent.menuItems[1].component;
    }
  }
}
</script>

<style scoped>
.home {
  background-color: var(--accent-color);
  border-radius: 10px;
  padding: 2rem;
  text-align: left;
  color: var(--text-color);
  margin-bottom: 2rem;
}

h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
  color: var(--main-color);
}

.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, auto);
  gap: 1rem;
}

.card {
  background-color: var(--accent-color);
  border-radius: 15px;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.logo { grid-area: 1 / 1 / 2 / 2; background-color: #FFA500; }
.post-task { grid-area: 1 / 2 / 2 / 3; background-color: #4169E1; }
.agents { grid-area: 1 / 3 / 2 / 5; background-color: #A0522D; }
.icons { grid-area: 2 / 1 / 3 / 2; background-color: #FF4500; }
.emoji { grid-area: 2 / 2 / 3 / 3; background-color: #FF69B4; }
.price { grid-area: 2 / 3 / 3 / 4; background-color: #8B4513; }
.services { grid-area: 2 / 4 / 3 / 5; background-color: #32CD32; }
.slogan { grid-area: 3 / 1 / 4 / 5; background-color: #FFD700; }

.agents {
  display: flex;
  justify-content: space-around;
}

.icon-group {
  display: flex;
  justify-content: space-around;
  width: 100%;
  margin-bottom: 1rem;
}

.icon-group span {
  font-size: 1.5rem;
}

.emoji span {
  font-size: 2rem;
  margin: 0 0.5rem;
}

.price h2 {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.price p {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.price small {
  font-size: 0.8rem;
}

.services ul {
  width: 100%;
  padding: 0;
  list-style-type: none;
}

.services li {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
}

.slogan h2 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.slogan p {
  font-size: 1rem;
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