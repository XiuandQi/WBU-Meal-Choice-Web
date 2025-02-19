<template>
    <MainTitle v-if="showDiv" />
    <Transition name="AllIndexDiv">
      <SubButtons v-if="!showSubButtons" @button-clicked="handleButtonClick" />
    </Transition>
    <SubButtonsList v-if="showSubButtons" :buttons="subButtons" @button-clicked="handleSubButtonClick" @go-back="handleGoBack"/>
    <!-- <GoBackButton v-if="showSubButtons" @go-back="handleGoBack" /> -->
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
</template>

<script>
import MainTitle from './components/MainTitle.vue';
import SubButtons from './components/SubButtons.vue';
import SubButtonsList from './components/SubButtonsList.vue';
// import GoBackButton from './components/GoBackButton.vue';
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
    // GoBackButton,
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
      const buttons_data = {
        "north_area":[
          { id: 'first_floorBtn', class: 'LeftBtn pop-up-button', words:'一楼' },
          { id: 'second_floorBtn', class: 'LeftBtn pop-up-button', words:'二楼' }
        ],
        "south_area":[
          { id: 'south_partBtn', class: 'LeftBtn pop-up-button', words:'南区' }
        ],
        "out_school":[
          { id: 'out_schoolBtn', class: 'LeftBtn pop-up-button', words:'校外' }
        ]
      }
      let newButtons = [];

      switch (clickedButtonId) {
        case IndexButtonId[0]:
          newButtons = [
            buttons_data.north_area[1],
            buttons_data.south_area[0],
            buttons_data.out_school[0]
          ];
          break;
        case IndexButtonId[1]:
          newButtons = [
            buttons_data.north_area[0],
            buttons_data.south_area[0],
            buttons_data.out_school[0]
          ];
          break;
        case IndexButtonId[2]:
          newButtons = [
            buttons_data.north_area[0],
            buttons_data.north_area[1],
            buttons_data.out_school[0]
          ];
          break;
        case IndexButtonId[3]:
          newButtons = [
            buttons_data.north_area[0],
            buttons_data.north_area[1],
            buttons_data.south_area[0]
          ];
          break;
      }

      return newButtons;
    }
  }
};
</script>