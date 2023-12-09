<template>
  <section class="faq scroll" id="faq">
    <div class="background">
      <img v-bind:class="{ faq__crowd }" class="background__crowd background__crowd--right"
        src="images/background__crowd--right.svg">
      <img v-bind:class="{ faq__icon }" class="background__icon background__icon--right"
        src="images/background__icon--right.svg">
    </div>
    <img src="images/faq__img.jpg" alt="" class="faq__img">
    <div class="faq__outer">
      <div class="faq__message">
        <p class="faq__text">回答をご覧いただけます。</p>
        <p class="faq__text">質問を押すと開閉し</p>
        <p class="faq__text">よくある質問集です。</p>
        <p class="faq__text">柴の宿に寄せられる</p>
      </div>
      <h2 class="faq__title">よくある質問</h2>
    </div>
    <ul class="faq__inner">
      <li class="faq__button" v-for="(item, index) in getQuestions" :key="item.id">
        <button type="button" class="faq__question" v-bind:class="{ 'faq__show': faq__show[index] }"
          @click="handleQuestion(index)">
          <p v-text="item.name" />
          <div class="faq__border">
            <span class="faq__border--vertical" v-bind:class="{ 'faq__transform': faq__show[index] }"></span>
            <span class="faq__border--beside"></span>
          </div>
          <div class="faq__bg"></div>
        </button>
        <p class="faq__answer" v-text="item.content" v-bind:class="{ 'faq__show': faq__show[index] }" />
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      //よくある質問に関する初期値
      faq__show: [],
      faq__transform: [],
      //表示・非表示に関する初期値
      faq__crowd: false,
      faq__icon: false,
    }
  },
  computed: {
    //よくある質問
    getQuestions() {
      const data = [
        {
          id: 1,
          name: 'Q: しばまるカフェってどんなところですか？',
          content: 'A: しばまるカフェは、和風の雰囲気で、可愛らしい柴犬たちと過ごすことができる癒しの空間です。心地よい店内で、お茶やスイーツを楽しみながら、柴犬たちと触れ合えます。',
        },
        {
          id: 2,
          name: 'Q: 柴犬たちと触れ合うことはできますか？',
          content: 'A: はい、もちろんです！店内には個性豊かな柴犬たちがおり、お客様は柴犬たちとふれあうことができます。柴犬たちはお客様を歓迎し、一緒に写真を撮ったり、触れ合ったりすることができます。',
        },
        {
          id: 3,
          name: 'Q: 予約は必要ですか？',
          content: 'A: 通常は予約は必要ありませんが、混雑が予想される場合や特別なイベント時には予約をおすすめしています。予約に関する詳細はウェブサイトやお電話でお問い合わせください。',
        },
        {
          id: 4,
          name: 'Q: 季節限定メニューはありますか？',
          content: 'A: 当店では季節限定のメニューもご用意していますが、一部の定番メニューもご好評いただいております。お気に入りのメニューが見つかることでしょう。',
        },
        {
          id: 5,
          name: 'Q: 柴犬カフェでのイベントはありますか？',
          content: 'A: はい、柴犬とのふれあいイベントや写真撮影プランなど、さまざまなイベントを開催しています。詳細なイベント情報は店内掲示やウェブサイトでご確認いただけます。',
        },
        {
          id: 6,
          name: 'Q: カフェ以外にも何か特別なサービスはありますか？',
          content: 'A: 柴犬のために用意した特別なおやつや、柴犬関連のグッズも販売しています。お土産やプレゼントにもおすすめです。',
        },
        {
          id: 7,
          name: 'Q: 子供やペット同伴は可能ですか？',
          content: 'A: はい、子供やペット同伴も歓迎しています。ただし、ペット同伴の場合は他の柴犬たちとの相性に留意してください。子供用のメニューもご用意しています。',
        },
        {
          id: 8,
          name: 'Q: 柴犬たちの健康管理はどのようにしていますか？',
          content: 'A: 柴犬たちの健康管理には細心の注意を払っています。専属の獣医師による健康チェックやワクチン接種を定期的に行っており、清潔で安全な環境を提供しています。',
        },
      ]
      return data
    },
  },
  created() {
    window.addEventListener("scroll", this.faqScroll);
  },
  methods: {
    // よくある質問を開閉する
    handleQuestion: function (index) {
      this.faq__show[index] = !this.faq__show[index],
        this.faq__transform[index] = !this.faq__transform[index]
    },
    //よくある質問のスクロール位置で表示・非表示制御
    faqScroll: function () {
      if (window.matchMedia('(min-width:768px)').matches) {
        //PC処理
        if (!this.faq__crowd) {
          this.faq__crowd = window.scrollY > 3900;
        } else if (window.scrollY <= 3900) {
          this.faq__crowd = !this.faq__crowd;
        }
        if (!this.faq__icon) {
          this.faq__icon = window.scrollY > 4200;
        } else if (window.scrollY <= 4200) {
          this.faq__icon = !this.faq__icon;
        }
      } else if (window.matchMedia('(max-width:767px)').matches) {
        //スマホ処理
        if (!this.faq__crowd) {
          this.faq__crowd = window.scrollY > 6100;
        } else if (window.scrollY <= 6100) {
          this.faq__crowd = !this.faq__crowd;
        }
        if (!this.faq__icon) {
          this.faq__icon = window.scrollY > 6100;
        } else if (window.scrollY <= 6100) {
          this.faq__icon = !this.faq__icon;
        }
      }
    },
  }
}
</script>
