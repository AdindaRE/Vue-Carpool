<template>
  <h1 v-html="formattedTitle"></h1>
</template>

<script>
export default {
  name: 'main_title',
  props: ['title'],
  computed: {
    formattedTitle() {
      return this.title.replace(/\n/g, '<br>');
    }
  }
};
</script>

<style>
h1 {
  font-family: 'Poppins';
  font-weight: normal;
  color: #ffffff;
}
</style>
