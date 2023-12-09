<template>
  <header class="header" id="header" v-bind:class="{ header__show }">
    <div class="header__outer">
      <a href="" class="header__logo">
        <h1>
          <img src="/images/header__logo.svg" alt="" class="header__icon">
        </h1>
      </a>
      <div class="header__unit">
        <div class="header__subunit">
          <p class="header__text">ご予約・ご相談はお電話で</p>
          <a href="tel:012-3456-7890" class="header__tel">TEL:012-3456-7890</a>
        </div>
        <button class="hamburger" id="hamburger" @click="hamburgerClick">
          <p class="hamburger__text">{{ menu ? 'MENU' : 'CLOSE' }}</p>
          <div class="hamburger__outer">
            <span class="hamburger__bar" v-bind:class="{ cross__top }" id="top"></span>
            <span class="hamburger__bar" v-bind:class="{ cross__middle }" id="middle"></span>
            <span class="hamburger__bar" v-bind:class="{ cross__bottom }" id="bottom"></span>
          </div>
        </button>
      </div>
    </div>
  </header>
  <div class="slide" id="slide" v-bind:class="{ slide__show }">
    <div class="slide__outer">
      <nav class="slide__nav">
        <a href="" class="slide__menu">先頭</a>
        <a @click="hamburgerClick" href="#concept" class="slide__menu">柴の宿の特徴</a>
        <a @click="hamburgerClick" href="#friend" class="slide__menu">柴の宿の仲間たち</a>
        <a @click="hamburgerClick" href="#food" class="slide__menu">柴の宿のお食事</a>
        <a @click="hamburgerClick" href="#faq" class="slide__menu">よくある質問</a>
        <a @click="hamburgerClick" href="#access" class="slide__menu">店舗情報</a>
      </nav>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      //ハンバーガーメニューの初期値
      slide__show: false,
      header__show: false,
      cross__top: false,
      cross__middle: false,
      cross__bottom: false,
      //ハンバーガーメニューの文字の初期値
      menu: true,
    }
  },
  methods: {
    //ハンバーガーメニュー開閉
    hamburgerClick: function () {
      //クラス名付与
      this.slide__show = !this.slide__show,
        this.header__show = !this.header__show,
        this.cross__top = !this.cross__top,
        this.cross__middle = !this.cross__middle,
        this.cross__bottom = !this.cross__bottom
      document.querySelector('body').classList.toggle("slide__none");
      //MENUのテキスト変更
      if (this.menu === true) {
        this.menu = false
      } else {
        this.menu = true
      }
    },
  }
}
</script>
