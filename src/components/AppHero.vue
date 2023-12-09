<template>
  <section class="hero container" id="hero">
    <img src="images/hero__img.png" alt="" class="hero__img">
    <img src="images/hero__moon.png" alt="" class="hero__moon">
    <h2 class="hero__title">
      <span v-for="(t, index) in title" :key="index" class="hero__span" :style="{ animationDelay: index * 100 + 'ms' }"
        v-text="t">
      </span>
    </h2>
    <div class="hero__position">
      <a href="#concept" class="hero__scroll">
        <p class="hero__txt">SCROLL</p>
      </a>
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      //メインタイトルの文字列
      title: '柴犬と癒しの空間',
    }
  }
}
</script>

