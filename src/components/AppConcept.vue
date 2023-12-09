<template>
  <section id="concept" class="concept">
    <div class="background">
      <img v-bind:class="{ concept__crowd }" class="background__crowd background__crowd--right"
        src="images/background__crowd--right.svg">
      <img v-bind:class="{ concept__icon }" class="background__icon background__icon--right"
        src="images/background__icon--right.svg">
      <img v-bind:class="{ concept__icon }" class="background__icon background__icon--left"
        src="images/background__icon--left.svg">
      <img v-bind:class="{ concept__crowd }" class="background__crowd background__crowd--left"
        src="images/background__crowd--left.svg">
    </div>
    <div class="container">
      <div class="concept__message">
        <p class="concept__text">柴の宿は、日本の伝統と現代の癒しを</p>
        <p class="concept__text">融合させた新しいスタイルのカフェです</p>
        <p class="concept__text">柴犬たちは皆、個性豊かで</p>
        <p class="concept__text">可愛らしい魅力があります。</p>
        <p class="concept__text">かわいらしい柴犬たちと柴犬との</p>
        <p class="concept__text">特別な時間をお楽しみください。</p>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      //表示・非表示に関する初期値
      concept__crowd: false,
      concept__icon: false,
    }
  },
  created() {
    window.addEventListener("scroll", this.conceptScroll);
  },
  methods: {
    //セクションコンセプトのスクロール位置で表示・非表示制御
    conceptScroll: function () {
      if (!this.concept__crowd) {
        this.concept__crowd = window.scrollY > 100;
      } else if (window.scrollY <= 0) {
        this.concept__crowd = !this.concept__crowd;
      }

      if (!this.concept__icon) {
        this.concept__icon = window.scrollY > 300;
      } else if (window.scrollY <= 300) {
        this.concept__icon = !this.concept__icon;
      }
    },
  },
}
</script>