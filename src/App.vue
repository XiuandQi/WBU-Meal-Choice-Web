<template>
  <div id="app">
    <MainTitle v-if="!showSubButtons" />
    <SubButtons v-if="!showSubButtons" @button-clicked="handleButtonClick" />
    <SubButtonsList v-if="showSubButtons" :buttons="subButtons" @button-clicked="handleSubButtonClick" />
    <GoBackButton v-if="showSubButtons" @go-back="handleGoBack" />
  </div>
</template>

<script>
import MainTitle from './components/MainTitle.vue';
import SubButtons from './components/SubButtons.vue';
import SubButtonsList from './components/SubButtonsList.vue';
import GoBackButton from './components/GoBackButton.vue';

export default {
  name: 'App',
  components: {
    MainTitle,
    SubButtons,
    SubButtonsList,
    GoBackButton
  },
  data() {
    return {
      showSubButtons: false,
      subButtons: []
    };
  },
  methods: {
    handleButtonClick(buttonId) {
      this.subButtons = this.generateSubButtons(buttonId);
      this.showSubButtons = true;
      document.getElementById('mainTitle').classList.add('move-and-shrink');
    },
    handleSubButtonClick(buttonId) {
      this.subButtons = this.generateSubButtons(buttonId);
    },
    handleGoBack() {
      this.showSubButtons = false;
      document.getElementById('mainTitle').classList.remove('move-and-shrink');
    },
    generateSubButtons(clickedButtonId) {
      const IndexButtonId = ['first_floorBtn', 'second_floorBtn', 'south_partBtn', 'out_schoolBtn'];
      let newButtons = [];

      switch (clickedButtonId) {
        case IndexButtonId[0]:
          newButtons = [
            { id: 'second_floorBtn', image: 'src/assets/image/second_floor.png',class: 'LeftBtnFirst pop-up-button' },
            { id: 'south_partBtn', image: 'src/assets/image/south_part.png' ,class: 'LeftBtnSecond pop-up-button' },
            { id: 'out_schoolBtn', image: 'src/assets/image/out_school.png' ,class: 'LeftBtnThree pop-up-button' }
          ];
          break;
        case IndexButtonId[1]:
          newButtons = [
            { id: 'first_floorBtn', image: 'src/assets/image/first_floor.png',class: 'LeftBtnFirst pop-up-button' },
            { id: 'south_partBtn', image: 'src/assets/image/south_part.png',class: 'LeftBtnSecond pop-up-button' },
            { id: 'out_schoolBtn', image: 'src/assets/image/out_school.png',class: 'LeftBtnThree pop-up-button' }
          ];
          break;
        case IndexButtonId[2]:
          newButtons = [
            { id: 'first_floorBtn', image: 'src/assets/image/first_floor.png',class: 'LeftBtnFirst pop-up-button' },
            { id: 'second_floorBtn', image: 'src/assets/image/second_floor.png',class: 'LeftBtnSecond pop-up-button' },
            { id: 'out_schoolBtn', image: 'src/assets/image/out_school.png',class: 'LeftBtnThree pop-up-button' }
          ];
          break;
        case IndexButtonId[3]:
          newButtons = [
            { id: 'first_floorBtn', image: 'src/assets/image/first_floor.png',class: 'LeftBtnFirst pop-up-button' },
            { id: 'second_floorBtn', image: 'src/assets/image/second_floor.png',class: 'LeftBtnSecond pop-up-button' },
            { id: 'south_partBtn', image: 'src/assets/image/south_part.png',class: 'LeftBtnThree pop-up-button' }
          ];
          break;
      }

      return newButtons;
    }
  }
};
</script>
