<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="flexColumn">
            <div
                v-for="(value, key) in floors_data.slice(0,5)"
                :key="key"
                :id="value"
                class="SouthFloorDiv"
                :class="{'choice':choiceId === key,'hidden':choiceId!=null && choiceId !== key}"
            >
            {{value}}
                <div style="font-size: 25px;">
                    <br>
                    {{getMealCardsHidden(key)}}
                </div>
            </div>
            <div class="SouthFloorDiv" 
                :class="{
                    'display_none':choiceId === null,'hidden':choiceId!=null && choiceId !== key
                }">
            </div>
        </div>
        <RollComponents :stores_data="floors_data" @RandomRoll="selectedIndexSync" @ResetSelection="selectedIndexSync"/>
    </div>
</template>
<script>
import RollComponents from './RollComponents.vue';
import stores_data from '../data/stores_data.json';
export default {
  name: 'SouthPartDiv',
  components: {
    RollComponents,
  },
  data(){
    return{
        choiceId: null,
        floors_data: stores_data.south_area,
    }
  },
  methods:{
    getMealCardsHidden(index){
        const NFMWH = [
            '一楼的面好像不错',
            '二楼未曾到访，不太熟悉',
            '三楼好像是有鸡公煲',
            '四楼没记错应该有烤肉',
            '五楼是不是有火锅'
        ];
        return NFMWH[index];
    },
    selectedIndexSync(index){
        this.choiceId = index;
    }
  }
}
</script>