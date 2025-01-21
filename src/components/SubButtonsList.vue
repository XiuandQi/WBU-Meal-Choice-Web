<template>
    <!-- <div class="juanzhouDiv" id="juanzhouDiv">
      <button v-for="button in buttons" :key="button.id" :id="button.id" class="juanzhouBtn pop-up-button" @click="handleClick(button.id)">
        <div class="container">
          <img :src="button.image" class="eatway">
        </div>
      </button>
    </div> -->
    <button v-for="button in buttons" :key="button.id" :id="button.id" :class="button.class" @click="handleClick(button.id)">
      <img :src="button.image" class="eatway">
    </button>
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