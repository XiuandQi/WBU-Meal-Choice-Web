<!-- 已弃用 -->
<template>
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
  </template>
  
  <script>
  export default {
    name: 'GoBackButton',
    methods: {
      handleGoBack() {
        this.$emit('go-back');
      }
    }
  };
  </script>