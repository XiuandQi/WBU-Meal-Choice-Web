<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="FoodsDivFrame">
          <TransitionGroup name="FoodDivs">
              <div 
                  v-for="(value,key,index) in stores_data.slice(0,8)" 
                  :key="key" 
                  :id="index" 
                  class="secondFloorFooddiv" 
                  :class="{ 'selected': selectedIndex === key, 'hidden': selectedIndex!=null && selectedIndex !== key }"
              >{{value}}</div>
              <div 
                  v-for="(value,key,index) in stores_data.slice(8,16)" 
                  :key="key" 
                  :id="index" 
                  class="secondFloorFooddiv" 
                  :class="{ 'selected': selectedIndex === key+8, 'hidden': selectedIndex!=null && selectedIndex !== key+8 }"
              >{{value}}</div>
          </TransitionGroup>
        </div>
        <RollComponents :stores_data="stores_data" @RandomRoll="selectedIndexSync" @ResetSelection="selectedIndexSync"/>
    </div>
</template>

<script>
import RollComponents from './RollComponents.vue';
import stores_data from '../data/stores_data.json';
export default {
  name: 'SecondFloorDiv',
  data() {
    return {
      selectedIndex: null,
      stores_data:stores_data.north_area[1],
    };
  },
  components: {
    RollComponents,
  },
  methods:{
    selectedIndexSync(index){
      this.selectedIndex = index;
    }
  }
};
</script>