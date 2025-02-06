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
                 {{ getMealWords(index) }}
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
                 {{ getMealWords(index + 8) }}
            </div>
        </div>
        <div class="secondFloorRestar">
            <button @click="RestartSelect" class="SFRestarBtn">
              <img src="../assets/image/restartbtn.png" class="restartIcon">
            </button>
        </div>
        <button @click="selectRandomDiv" class="choiceBtn1">
          抽&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;取
        </button>
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
    getMealWords(index){
      const SFMW = [
        '鄉米先生','匠心卤','合利家韩餐','三汁焖锅','熊叫','满口香小碗菜','莫小喃水饺',
        '土豆泥拌饭','轻食主义','馄饨','兰州拉面','好吃佬炒饭','湖南小炒饭','张亮麻辣烫',
        '捞面馆','面食主义'
      ];
      return SFMW[index];
    }
  }
};
</script>