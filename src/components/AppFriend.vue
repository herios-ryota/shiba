<template>
  <section class="friend scroll" id="friend">
    <img src="images/friend__img.jpg" alt="" class="friend__img">
    <div class="friend__outer">
      <div class="friend__message">
        <p class="friend__text">ほっこりと温かくすることでしょう。</p>
        <p class="friend__text">どの柴犬もあなたの心を</p>
        <p class="friend__text">柴の宿の仲間たち。</p>
        <p class="friend__text">温かなほほえみをお届けする</p>
        <p class="friend__text">可愛らしいキャラクターを持っています。</p>
        <p class="friend__text">柴犬たちも、それぞれが個性的で</p>
      </div>
      <h2 class="friend__title">柴の宿の仲間たち</h2>
    </div>
    <div class="friend__inner">
      <div class="friend__unit" v-for="friend in friends" :key="friend.id">
        <img v-if="friend.dogImage" :src="friend.dogImage" class="friend__image">
        <p class="friend__name">{{ friend.dogName }}</p>
        <p class="friend__detail" v-html="htmlText(friend.message)"></p>
      </div>
    </div>
    <button class="submit" v-if="(friends.length - count) >= 0" type="button" @click="submitMore">
      <span class="submit__border submit__border--top"></span>
      <span class="submit__border submit__border--right"></span>
      <p class="submit__text">もっと柴犬を見る</p>
      <span class="submit__border submit__border--bottom"></span>
      <span class="submit__border submit__border--left"></span>
    </button>
    <div class="background">
      <img v-bind:class="{ friend__crowd }" class="background__crowd background__crowd--right"
        src="images/background__crowd--right.svg">
      <img v-bind:class="{ friend__icon }" class="background__icon background__icon--right"
        src="images/background__icon--right.svg">
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      //表示・非表示に関する初期値
      friend__crowd: false,
      friend__icon: false,
      count: 3,
      dog: [
        {
          id: 1,
          dogImage: 'images/friend__image01.png',
          dogName: 'しろ（Shiro）',
          message:
            `真っ白な、美しく優雅な柴犬、しろ。雪が舞うような芳醇な雰囲気と、品のある立ち居振る舞いが彼女の魅力です。訪れる皆さんに癒しと優雅なひとときをお届けします。
            特徴:
            ・優雅な歩き方と、気品漂う姿勢。
            ・透明感のある真っ白な毛並み。
            ・穏やかで優しい表情。
            好きなこと:
            ・お茶うけの和菓子を食べること。
            ・空を見上げながらのんびりすること。`,
        },
        {
          id: 2,
          dogImage: 'images/friend__image02.png',
          dogName: 'わらび（Warabi）',
          message:
            `元気いっぱいの柴犬冒険者、わらび。彼の好奇心旺盛な性格と、どこまでも走り回る元気さが、カフェを訪れる皆さんに活気と笑顔をもたらします。
          特徴:
          ・しっぽを高らかに振りながら走る姿勢。
          ・元気いっぱいの笑顔と大きな瞳。
          好きなこと:
          ・カフェの庭でボール遊びをすること。
          ・新しい友達とのふれあい。`,
        },
        {
          id: 3,
          dogImage: 'images/friend__image03.png',
          dogName: 'もも（Momo）',
          message:
            `元気いっぱいの柴犬冒険者、わらび。彼の好奇心旺盛な性格と、どこまでも走り回る元気さが、カフェを訪れる皆さんに活気と笑顔をもたらします。
            特徴:
            ・しっぽを高らかに振りながら走る姿勢。
            ・元気いっぱいの笑顔と大きな瞳。
            好きなこと: 
            ・カフェの庭でボール遊びをすること。
            ・新しい友達とのふれあい。`,
        },
        {
          id: 4,
          dogImage: 'images/friend__image04.png',
          dogName: 'こてつ (Kotetsu)',
          message:
            `知的で好奇心旺盛な男の子。お客様の手の中に鼻を突っ込み、新しい匂いや感触を楽しむことが大好き。
            特徴:
            ・小さいサイズながら、頭の良さが際立つ。トリックやお手を得意とし、お客様を驚かせることも。
            好きなこと:
            ・お客様の手を舐めるのが好き。
            ・新しいおもちゃで遊ぶのも大好き。
          `,
        },
        {
          id: 5,
          dogImage: 'images/friend__image05.png',
          dogName: 'ひなた (Hinata)',
          message:
            `おおらかでおっとりとした性格の女の子。日向ぼっこが好きで、穏やかな陽射しの中でのんびり過ごすのが幸せ。
            特徴:
            ・まん丸の瞳が愛らしい。
            ・お客様の隣でくつろぎながら、微笑ましい姿勢でまったり。
            好きなこと:
            ・膝に乗ってくつろぐのが好き。
            ・お客様との触れ合いで心地よいひとときを過ごす。
            `,
        },
      ],
    }
  },
  computed:{
    friends() {
      const dog = this.dog
      return dog.slice(0, this.count)
    }
  },
  created() {
    window.addEventListener("scroll", this.friendScroll);
  },
  methods: {
    //オブジェクト内brを使用できる様に
    htmlText(msg) {
      var message = !!(msg);
      if (message) {
        return msg.replace(/\r?\n/g, '<br>')
      }
    },
    // buttonをクリックするとcountが増えていく。結果listItemsの数が増えて表示されていく。
    submitMore() {
      this.count += 3
    },
    //柴の宿の仲間たちのスクロール位置で表示・非表示制御
    friendScroll: function () {
      if (window.matchMedia('(min-width:768px)').matches) {
        //PC処理
        if (!this.friend__crowd) {
          this.friend__crowd = window.scrollY > 2000;
        } else if (window.scrollY <= 2000) {
          this.friend__crowd = !this.friend__crowd;
        }
      } else if (window.matchMedia('(max-width: 767px)').matches) {
        //スマホ処理
        if (!this.friend__crowd) {
          this.friend__crowd = window.scrollY > 4000;
        } else if (window.scrollY <= 3700) {
          this.friend__crowd = !this.friend__crowd;
        }
      }

      if (window.matchMedia('(min-width:768px)').matches) {
        //PC処理
        if (!this.friend__icon) {
          this.friend__icon = window.scrollY > 2300;
        } else if (window.scrollY <= 2300) {
          this.friend__icon = !this.friend__icon;
        }
      } else if (window.matchMedia('(max-width: 767px)').matches) {
        //スマホ処理
        if (!this.friend__icon) {
          this.friend__icon = window.scrollY > 4200;
        } else if (window.scrollY <= 4000) {
          this.friend__icon = !this.friend__icon;
        }
      }
    },
  },
}
</script>
