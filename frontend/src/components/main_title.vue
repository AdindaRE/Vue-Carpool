<template>
      <h1> {{ title }}</h1>
  </template>
  
  <script>
  export default {
  name: 'main_title',
  props: ['title']};
  </script>

  <style>
h1{
  font-family: 'Poppins';
  font-weight: normal;
  color: #1B2B71;

}
</style>