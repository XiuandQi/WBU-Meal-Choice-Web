<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="firstMealDiv">
            <div>
                <!-- {{ currentWords }} -->
                  {{ stores_data[currentWords] }}
            </div>
        </div>
        <RollComponents :stores_data="stores_data" @RandomRoll="showRandomImage" @ResetSelection="showRandomImage"/>
    </div>
</template>
<script>
import RollComponents from './RollComponents.vue';
import stores_data from '../data/stores_data.json';
export default {
    name: 'FirstFloorDiv',
    data(){
        return{
            currentWords:null,
            stores_data:stores_data.north_area[0],
        }
    },
    components:{
        RollComponents,
    },
    methods:{
        showRandomImage(index){
            this.currentWords = index;
        }
    }
}

</script>