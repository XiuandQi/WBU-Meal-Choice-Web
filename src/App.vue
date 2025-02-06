<template>
  <div id="app">
    <MainTitle v-if="showDiv" />
    <Transition name="AllIndexDiv">
      <SubButtons v-if="!showSubButtons" @button-clicked="handleButtonClick" />
    </Transition>
    <SubButtonsList v-if="showSubButtons" :buttons="subButtons" @button-clicked="handleSubButtonClick" />
    <GoBackButton v-if="showSubButtons" @go-back="handleGoBack" />
    <Transition name="AllScreenDiv1">
      <FirstFloorDiv v-if="showFirstBtn" />
    </Transition>
    <Transition name="AllScreenDiv2">
      <SecondFloorDiv v-if="showSecondBtn" />
    </Transition>
    <Transition name="AllScreenDiv3">
      <SouthPartDiv v-if="showSouthBtn" />
    </Transition>
    <Transition name="AllScreenDiv4">
      <OutSchoolDiv v-if="showOutBtn" />
    </Transition>
  </div>
</template>

<script>
import MainTitle from './components/MainTitle.vue';
import SubButtons from './components/SubButtons.vue';
import SubButtonsList from './components/SubButtonsList.vue';
import GoBackButton from './components/GoBackButton.vue';
import FirstFloorDiv from './components/FirstFloorDiv.vue';
import SecondFloorDiv from './components/SecondFloorDiv.vue';
import SouthPartDiv from './components/SouthPartDiv.vue';
import OutSchoolDiv from './components/OutSchoolDiv.vue';

export default {
  name: 'App',
  components: {
    MainTitle,
    SubButtons,
    SubButtonsList,
    GoBackButton,
    FirstFloorDiv,
    SecondFloorDiv,
    SouthPartDiv,
    OutSchoolDiv
  },
  data() {
    return {
      showSubButtons: false,
      subButtons: [],
      showDiv:true,
      showFirstBtn:false,
      showSecondBtn:false,
      showSouthBtn:false,
      showOutBtn:false
    };
  },
  methods: {
    handleButtonClick(buttonId) {
      this.showSubButtons = true;
      document.getElementById('mainTitle').classList.add('move-and-shrink');
      this.updataButtonVisibility(buttonId);
    },
    handleSubButtonClick(buttonId) {
      this.updataButtonVisibility(buttonId);
      
    },
    updataButtonVisibility(buttonId){
      this.subButtons = this.generateSubButtons(buttonId);
      this.showFirstBtn = buttonId === 'first_floorBtn';
      this.showSecondBtn = buttonId === 'second_floorBtn';
      this.showSouthBtn = buttonId === 'south_partBtn';
      this.showOutBtn = buttonId === 'out_schoolBtn';
    },

    handleGoBack() {
      this.showSubButtons = false;
      this.showFirstBtn = false;
      this.showSecondBtn = false;
      this.showSouthBtn = false;
      this.showOutBtn = false;
      document.getElementById('mainTitle').classList.remove('move-and-shrink');
    },


    generateSubButtons(clickedButtonId) {
      const IndexButtonId = ['first_floorBtn', 'second_floorBtn', 'south_partBtn', 'out_schoolBtn'];
      let newButtons = [];

      switch (clickedButtonId) {
        case IndexButtonId[0]:
          newButtons = [
            { id: 'second_floorBtn',class: 'LeftBtnFirst pop-up-button', words:'二          楼' },
            { id: 'south_partBtn', class: 'LeftBtnSecond pop-up-button', words:'南          区' },
            { id: 'out_schoolBtn', class: 'LeftBtnThree pop-up-button', words:'校          外' }
          ];
          break;
        case IndexButtonId[1]:
          newButtons = [
            { id: 'first_floorBtn', class: 'LeftBtnFirst pop-up-button', words:'一          楼' },
            { id: 'south_partBtn', class: 'LeftBtnSecond pop-up-button', words:'南          区' },
            { id: 'out_schoolBtn', class: 'LeftBtnThree pop-up-button', words:'校          外' }
          ];
          break;
        case IndexButtonId[2]:
          newButtons = [
            { id: 'first_floorBtn', class: 'LeftBtnFirst pop-up-button', words:'一          楼' },
            { id: 'second_floorBtn', class: 'LeftBtnSecond pop-up-button', words:'二          楼' },
            { id: 'out_schoolBtn', class: 'LeftBtnThree pop-up-button', words:'校          外' }
          ];
          break;
        case IndexButtonId[3]:
          newButtons = [
            { id: 'first_floorBtn', class: 'LeftBtnFirst pop-up-button', words:'一          楼' },
            { id: 'second_floorBtn', class: 'LeftBtnSecond pop-up-button', words:'二          楼' },
            { id: 'south_partBtn', class: 'LeftBtnThree pop-up-button', words:'南          区' }
          ];
          break;
      }

      return newButtons;
    }
  }
};
</script>