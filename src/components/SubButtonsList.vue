<template>
  <div id="leftButtons">
    <button v-for="button in buttons" :key="button.id" :id="button.id" :class="button.class" @click="handleClick(button.id)">
      <img :src="button.image" class="eatway">
    </button>
  </div>
  </template>
  
  <script>
  export default {
    name: 'SubButtonsList',
    props: {
      buttons: {
        type: Array,
        required: true
      }
    },
    methods: {
      handleClick(buttonId) {
        this.$emit('button-clicked', buttonId);
      }
    }
  };
  </script>