<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div>
            <div
                v-for="(card, index) in cards.slice(0,5)"
                :key="index"
                :id="card"
                class="SouthFloorDiv"
                :class="{'choice':choiceId === card,'hidden':choiceId && choiceId !== card}"
            >
            {{ getMealCards(index) }}
            <div style="font-size: 25px;">
                <br>
                {{getMealCardsHidden(index)}}
            </div>
            </div>
        </div>
        <div class="secondFloorRestar">
            <button @click="RestartChoice" class="SFRestarBtn">
              <img src="../assets/image/restartbtn.png" class="restartIcon">
            </button>
        </div>
        <button @click="choiceRandomCard" class="choiceBtn1">
          抽&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;取
        </button>
    </div>
</template>
<script>
export default {
  name: 'SouthPartDiv',
  data(){
        return{
            choiceId: null,
            cards: [
                'SouthFloor1', 'SouthFloor2', 'SouthFloor3', 'SouthFloor4', 'SouthFloor5',
            ]

    }
  },
  methods:{
    choiceRandomCard(){
        const randomIndex = Math.floor(Math.random() * this.cards.length);
        this.choiceId = this.cards[randomIndex];
    },
    RestartChoice(){
        this.choiceId = null;
    },
    getMealCards(index){
        const NFMW = [
            '一          楼','二          楼','三          楼','四          楼','五          楼'
        ];
        return NFMW[index];
    },
    getMealCardsHidden(index){
        const NFMWH = [
            '一楼的面好像不错',
            '二楼未曾到访，不太熟悉',
            '三楼好像是有鸡公煲',
            '四楼没记错应该有烤肉',
            '五楼是不是有火锅'
        ];
        return NFMWH[index];
    }
    
  }
}
</script>