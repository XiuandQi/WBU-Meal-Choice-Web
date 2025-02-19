<template>
  <div class="LeftBtnsContainer">
    <div id="leftButtons">
      <button v-for="button in buttons" :key="button.id" :id="button.id" :class="button.class" @click="handleClick(button.id)">
        <div class="LeftBtnWords">
        {{ button.words }}
        </div>
      </button>
    </div>
    <div class="gobackBtnDiv left-go-on">
        <button class="gobackBtn" @click="handleGoBack">
          <span>
            <img src="../assets/image/gobackicon2.png" class="gobackIcon">
          </span>
          <span>
            <div class="getbackWord">
              返&nbsp;&nbsp;回
            </div>
          </span>
        </button>
      </div>
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
      },
      handleGoBack() {
        this.$emit('go-back');
      }
    }
  };
  </script>