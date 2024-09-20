<template>
  <div class="about">
    <h2>회사 소개</h2>
    <p>저희는 2010년부터 원룸 중개 서비스를 제공해온 전문 기업입니다.</p>
    <p>고객의 니즈에 맞는 최적의 원룸을 찾아드리는 것이 저희의 목표입니다.</p>
    <h3>연락처</h3>
    <p>이메일: info@oneroom.com</p>
    <p>전화: 02-1234-5678</p>
  </div>
</template>

<script>
export default {
  name: 'AboutPage'
}
</script>

<style scoped>
.about {
  border-radius: 10px;
  padding: 2rem;
  color: var(--text-color);
}

h2, h3 {
  color: var(--main-color);
}
</style>