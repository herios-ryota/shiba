<template>
  <section class="access scroll" id="access">
    <div class="background">
      <img v-bind:class="{ access__crowdRight }" class="background__crowd background__crowd--right"
        src="images/background__crowd--right.svg">
      <img v-bind:class="{ access__iconRight }" class="background__icon background__icon--right"
        src="images/background__icon--right.svg">
      <img v-bind:class="{ access__iconLeft }" class="background__icon background__icon--left"
        src="images/background__icon--left.svg">
      <img v-bind:class="{ access__crowdLeft }" class="background__crowd background__crowd--left"
        src="images/background__crowd--left.svg">
    </div>
    <img src="images/access__img.jpg" alt="" class="food__img">
    <div class="food__outer">
      <div class="food__message">
        <p class="food__text">最寄駅や営業時間などお確かめ下さい。</p>
        <p class="food__text">お過ごしいただけます。</p>
        <p class="food__text">柴犬たちと一緒に心地よいひとときを</p>
        <p class="food__text">和風の趣き漂う店内で</p>
      </div>
      <h2 class="food__title">店舗情報</h2>
    </div>
    <div class="access__inner">
      <iframe class="access__map"
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1621.0096856657788!2d139.74051190166603!3d35.651894366292375!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x60188bbbb41922f3%3A0x33ebfd75f2f06cac!2z5p2x5Lqs6YO95riv5Yy6!5e0!3m2!1sja!2sjp!4v1701794045571!5m2!1sja!2sjp"
        width="100%" height="300">
      </iframe>
      <p class="access__txt">
        <strong class="access__strong">柴の宿</strong><br>
        <span class="access__item">住所</span><br>
        〒123-4567 東京都港区柴犬町1-2-3 <br>
        <span class="access__item">電話番号</span><br>
        012-3456-7890 <br>
        <span class="access__item">営業時間</span><br>
        平日: 11:00 - 19:00土日祝: 10:00 - 20:00 <br>
        <span class="access__item">アクセス</span><br>
        電車: 品川駅から徒歩10分<br>
        車: 駐車場あり（近隣に提携駐車場も利用可能） <br>
        <span class="access__item">公共交通機関ご利用の方へ</span><br>
        最寄りの駅からは徒歩圏内にあります。電車やバスをご利用いただくと、便利にお越しいただけます。<br>
        <span class="access__item">お車でお越しの方へ</span><br>
        駐車場がございますので、お車でのご来店も可能です。駅周辺には提携駐車場もございますので、そちらもご利用いただけます。<br>
        アクセスに関する詳細は、お電話にてお問い合わせいただくか、地図をご確認ください。
      </p>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      access__crowdLeft: false,
      access__iconLeft: false,
      access__crowdRight: false,
      access__iconRight: false,
    }
  },
  created() {
    window.addEventListener("scroll", this.accessScrollLeft);
    window.addEventListener("scroll", this.accessScrollRight);
  },
  methods: {
    //店舗情報のスクロール位置で表示・非表示制御
    accessScrollLeft: function () {
      if (window.matchMedia('(min-width:768px)').matches) {
        //PC処理
        if (!this.access__iconLeft) {
          this.access__iconLeft = window.scrollY > 5800;
        } else if (window.scrollY <= 5900) {
          this.access__iconLeft = !this.access__iconLeft;
        }
        if (!this.access__crowdLeft) {
          this.access__crowdLeft = window.scrollY > 5800;
        } else if (window.scrollY <= 5900) {
          this.access__crowdLeft = !this.access__crowdLeft;
        }
      } else if (window.matchMedia('(max-width:768px)').matches) {
        //スマホ処理
        if (!this.access__iconLeft) {
          this.access__iconLeft = window.scrollY > 7600;
        } else if (window.scrollY <= 7600) {
          this.access__iconLeft = !this.access__iconLeft;
        }
        if (!this.access__crowdLeft) {
          this.access__crowdLeft = window.scrollY > 7700;
        } else if (window.scrollY <= 7700) {
          this.access__crowdLeft = !this.access__crowdLeft;
        }
      }
    },
    accessScrollRight: function () {
      if (window.matchMedia('(min-width:768px)').matches) {
        //PC処理
        if (!this.access__crowdRight) {
          this.access__crowdRight = window.scrollY > 5800;
        } else if (window.scrollY <= 6500) {
          this.access__crowdRight = !this.access__crowdRight;
        }
        if (!this.access__iconRight) {
          this.access__iconRight = window.scrollY > 5800;
        } else if (window.scrollY <= 6500) {
          this.access__iconRight = !this.access__iconRight;
        }
      } else if (window.matchMedia('(max-width:767px)').matches) {
        //スマホ処理
        if (!this.access__crowdRight) {
          this.access__crowdRight = window.scrollY > 8600;
        } else if (window.scrollY <= 8600) {
          this.access__crowdRight = !this.access__crowdRight;
        }
        if (!this.access__iconRight) {
          this.access__iconRight = window.scrollY > 8800;
        } else if (window.scrollY <= 8800) {
          this.access__iconRight = !this.access__iconRight;
        }
      }
    }
  }
}
</script>