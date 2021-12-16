<template>
  <div class="about">
    <section class="hero">
      <div class="hero-text container">
        <h4>뷰 템플릿</h4>
        <hr />
        <h2>포트폴리오 화면 <br />입니다<br /></h2>
        <hr />
      </div>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'About',
  components: {},
}
</script>

<style lang="css" scoped>
.hero {
  background-image: url('../assets/hero-bg.png');
  background-attachment: fixed;
  position: relative;
  height: 100vh;
  text-align: center;
}

.hero img {
  object-fit: cover;
  height: 100%;
  width: 100%;
}

.hero .hero-text {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: #fff;
}

.hero .hero-text h4 {
  text-transform: uppercase;
  font-size: 22px;
  padding-bottom: 4px;
}

.hero .hero-text h2 {
  font-size: 50px;
}

@media (min-width: 550px) {
  .hero .hero-text {
    font-size: 80px;
  }
}

.hero hr:nth-child(2) {
  max-width: 365px;
  margin-bottom: 16px;
}

.hero hr:nth-child(4) {
  height: 6px;
  background-color: #fff;
  border: none;
  max-width: 85px;
  margin-top: 16px;
}
</style>
