<script>
export default {
  components: {
    main_title,
    message,
    navbar
  },
  methods: {
    onClick() {
      this.$router.push('/Messages');
    }
  }
}
import main_title from '../components/main_title.vue';
import message from '../components/message.vue';
import navbar from '../components/navbar.vue';
</script>

<template>
  <main_title title="Messages" />
  <div @click="onClick">
    <message />
  </div>
  <navbar />
</template>

<style></style>
