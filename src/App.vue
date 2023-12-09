<script setup>
import AppHeader from "./components/AppHeader.vue";
import AppHero from "./components/AppHero.vue";
import AppConcept from "./components/AppConcept.vue";
import AppFriend from "./components/AppFriend.vue";
import AppFood from "./components/AppFood.vue";
import AppFaq from "./components/AppFaq.vue";
import AppAccess from "./components/AppAccess.vue";
import AppFooter from "./components/AppFooter.vue";
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=M+PLUS+Rounded+1c:wght@400;500;700&family=Zen+Old+Mincho:wght@400;500;700&display=swap');
</style>
<template>
  <div class="wrap" v-cloak>
    <AppHeader />
    <main class="main" id="main">
      <AppHero />
      <AppConcept />
      <AppFriend />
      <AppFood />
      <AppFaq />
      <AppAccess />
    </main>
    <AppFooter />
  </div>
</template>

