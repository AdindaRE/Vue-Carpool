<script>
import main_title from '../components/main_title.vue';
import card from '../components/card.vue';
import navbar from '../components/navbar.vue';
import subtitle from '../components/subtitle.vue';
import banner from '../components/banner.vue';

export default {
  components: {
    main_title, card, navbar, subtitle, banner
  }
  ,
  data() {
    return {
      titleText: "Hi, Selena!👋🏾\nReady for Takeoff?"
    };
  }
};
</script>

<template>
    <main_title :title="titleText" />
    <div class="margin-top">
    <subtitle/></div>
    <card :items="cards" />
    <banner/>
<navbar/>
</template>

<style>
.margin-top{
margin-top: 15px;
}
</style>