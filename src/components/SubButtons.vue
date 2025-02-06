<template>
    <div class="juanzhouDiv juanzhouBtnDiv_move" id="juanzhouDiv">
      <button class="juanzhouBtn" id="first_floorBtn" @click="handleClick('first_floorBtn')">
        <div class="container">
           一&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;楼
        </div>
      </button>
      <button class="juanzhouBtn" id="second_floorBtn" @click="handleClick('second_floorBtn')">
        <div class="container">
          二&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;楼
        </div>
      </button>
      <button class="juanzhouBtn" id="south_partBtn" @click="handleClick('south_partBtn')">
        <div class="container">
          南&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;区
        </div>
      </button>
      <button class="juanzhouBtn" id="out_schoolBtn" @click="handleClick('out_schoolBtn')">
        <div class="container">
          校&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;外
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