<template>
    <div class="juanzhouDiv juanzhouBtnDiv_move" id="juanzhouDiv">
      <button class="juanzhouBtn" id="first_floorBtn" @click="handleClick('first_floorBtn')">
        <div class="container">
          <img src="../assets/image/first_floor.png" class="eatway">
        </div>
      </button>
      <button class="juanzhouBtn" id="second_floorBtn" @click="handleClick('second_floorBtn')">
        <div class="container">
          <img src="../assets/image/second_floor.png" class="eatway">
        </div>
      </button>
      <button class="juanzhouBtn" id="south_partBtn" @click="handleClick('south_partBtn')">
        <div class="container">
          <img src="../assets/image/south_part.png" class="eatway">
        </div>
      </button>
      <button class="juanzhouBtn" id="out_schoolBtn" @click="handleClick('out_schoolBtn')">
        <div class="container">
          <img src="../assets/image/out_school.png" class="eatway">
        </div>
      </button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SubButtons',
    methods: {
      handleClick(buttonId) {
        this.$emit('button-clicked', buttonId);
      }
    }
  };
  </script>