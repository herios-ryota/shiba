<template>
  <section class="food scroll" id="food">
    <div class="background">
      <img v-bind:class="{ food__icon }" class="background__icon background__icon--left"
        src="images/background__icon--left.svg">
    </div>
    <img src="images/food__img.jpg" alt="" class="food__img">
    <div class="food__outer">
      <div class="food__message">
        <p class="food__text">お客様の好みに合わせて選べます</p>
        <p class="food__text">シンプルで落ち着いた雰囲気の洋室があり</p>
        <p class="food__text">座席は畳敷きの和室と</p>
        <p class="food__text">木の温もりを感じる心地よい空間が広がっています。</p>
        <p class="food__text">店内は、淡い和風の照明が柔らかな光を差し込ませ</p>
      </div>
      <h2 class="food__title">柴の宿のお食事</h2>
    </div>
    <div class="food__inner">
      <div class="food__unit">
        <p class="food__item">お飲み物</p>
        <div class="food__subitem">
          <p class="food__name">桜らんまん茶</p>
          <p class="food__price">500円</p>
        </div>
        <div class="food__subitem">
          <p class="food__name">抹茶ラテ</p>
          <p class="food__price">600円</p>
        </div>
        <div class="food__subitem">
          <p class="food__name">柴氷コーヒー</p>
          <p class="food__price">550円</p>
        </div>
        <div class="food__subitem">
          <p class="food__name">和風アイスティー</p>
          <p class="food__price">450円</p>
        </div>
      </div>
      <div class="food__unit">
        <p class="food__item">おやつ</p>
        <div class="food__subitem">
          <p class="food__name">しばしばクッキーセット</p>
          <p class="food__price">800円</p>
        </div>
        <div class="food__subitem">
          <p class="food__name">和風和菓子アソート</p>
          <p class="food__price">900円</p>
        </div>
        <div class="food__subitem">
          <p class="food__name">柴犬アイスクリーム</p>
          <p class="food__price">700円</p>
        </div>
      </div>
      <div class="food__unit">
        <p class="food__item">ランチセット</p>
        <div class="food__subitem">
          <p class="food__name">しばまるランチセット</p>
          <p class="food__price">1,200円</p>
        </div>
        <p class="food__item">デザートプレート</p>
        <div class="food__subitem">
          <p class="food__name">柴犬デザートプレート</p>
          <p class="food__price">1,000円</p>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      //表示・非表示に関する初期値
      food__icon: false,
    }
  },
  created() {
    window.addEventListener("scroll", this.foodScroll);
  },
  methods: {
    //柴の宿のお食事のスクロール位置で表示・非表示制御
    foodScroll: function () {
      if (window.matchMedia('(min-width:768px)').matches) {
        //PC処理
        if (!this.food__icon) {
          this.food__icon = window.scrollY > 3200;
        } else if (window.scrollY <= 3200) {
          this.food__icon = !this.food__icon;
        }
      } else if (window.matchMedia('(max-width:767px)').matches) {
        //スマホ処理
        if (!this.food__icon) {
          this.food__icon = window.scrollY > 5000;
        } else if (window.scrollY <= 4800) {
          this.food__icon = !this.food__icon;
        }
      }
    },
  }
}
</script>