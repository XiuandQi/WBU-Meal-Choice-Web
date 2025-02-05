<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="secondFloorFoodDiv">
            <div 
                v-for="(id, index) in divIds.slice(0, 8)" 
                :key="id" 
                :id="id" 
                class="secondFloorFooddiv" 
                :class="{ 'selected': selectedId === id, 'hidden': selectedId && selectedId !== id }"
            >
                <img :src="getImageSrc(index)" class="secondFloorFoodImg">
            </div>
        </div>
        <div class="secondFloorFoodDiv">
            <div 
                v-for="(id, index) in divIds.slice(8, 16)" 
                :key="id" 
                :id="id" 
                class="secondFloorFooddiv" 
                :class="{ 'selected': selectedId === id, 'hidden': selectedId && selectedId !== id }"
            >
                <img :src="getImageSrc(index + 8)" class="secondFloorFoodImg">
            </div>
        </div>
        <div class="secondFloorRestar">
            <button @click="RestartSelect" class="SFRestarBtn">
                <img src="../assets/image/restartbtn.png" class="restartIcon">
            </button>
        </div>
        <div class="choiceBtnDiv">
            <button @click="selectRandomDiv" class="choiceBtn">
                <img src="../assets/image/choice_btn.png" class="choiceBtnImg">
            </button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'SecondFloorDiv',
  data() {
    return {
      selectedId: null,
      divIds: [
        'SFFD1', 'SFFD2', 'SFFD3', 'SFFD4', 'SFFD5', 'SFFD6', 'SFFD7', 'SFFD8',
        'SFFD9', 'SFFD10', 'SFFD11', 'SFFD12', 'SFFD13', 'SFFD14', 'SFFD15', 'SFFD16'
      ]
    };
  },
  methods: {
    selectRandomDiv() {
      const randomIndex = Math.floor(Math.random() * this.divIds.length);
      this.selectedId = this.divIds[randomIndex];
    },

    RestartSelect() {
      this.selectedId = null;
    },

    getImageSrc(index) {
      const images = [
        'xiangmixianshen.png', 'jiangxinlu.png', 'hejialihancan.png', 'sanzimenguo.png',
        'xiongjiao.png', 'mankouxiangxiaowancai.png', 'moxiaonanshuijiao.png', 'tudounibanfan.png',
        'qingshizuyi.png', 'huntun.png', 'lanzhoulamian.png', 'haochilaochaofan.png',
        'hunanxiaochaofan.png', 'zhangliangmalatang.png', 'laomianguan.png', 'mianshizuyi.png'
      ];
      return images[index].startsWith('/') ? images[index] : `/src/assets/image/secondfloor/${images[index]}`;
    }
  }
};
</script>