<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="FoodsDivFrame">
          <TransitionGroup name="FoodDivs">
              <div 
                  v-for="(value,key,index) in stores_data" 
                  :key="key" 
                  :id="index" 
                  class="OutSchoolDiv" 
                  :class="{ 'selected': selectedIndex === key, 'hidden': selectedIndex!=null && selectedIndex !== key }"
              >{{value}}</div>
          </TransitionGroup>
        </div>
        <div class="HiddenTips" v-if="selectedIndex === 1">
            <span>
              都校外了，不去吃大餐可惜了吧
            </span>
          </div>
        <!-- <div>
          <div class="OutSchoolDiv">
            <span>
              外卖/后街
            </span>
          </div>
          <div class="OutSchoolDiv">
            <span>
              直接吃大餐
            </span>
          </div>

        </div> -->
        <!-- <div class="rollDiv">
          <button class="rollBtn" @click="showHiddenTips">抽<span>取</span></button>
        </div> -->
        <RollComponents :stores_data="stores_data" :Roll="selectedIndexSync" :Reset="selectedIndexSync"></RollComponents>
    </div>
</template>
<script>
import stores_data from '../data/stores_data.json';
import RollComponents from './RollComponents.vue';
export default {
  name: 'OutSchoolDiv',
  components: {
    RollComponents,
  },
  data(){
    return{
      stores_data:stores_data.out_school,
      selectedIndex: null
    }
  },
  methods:{
    showHiddenTips(){
      let hiddenTips = document.querySelector('.HiddenTips');
      hiddenTips.classList.toggle('HiddenTips_show');
    },
    selectedIndexSync(index){
      this.selectedIndex = index;
    }
  }
}
</script>