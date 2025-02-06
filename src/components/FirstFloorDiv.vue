<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="firstMealDiv">
             {{ currentWords }}
        </div>
        <button @click="showRandomImage" class="choiceBtn1">
          抽&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;取
        </button>
    </div>
</template>
<script>
export default {
    name: 'FirstFloorDiv',
    data(){
        return{
            FFMW:[
                '自助餐',
                '天天价特色菜',
                '民族窗口'
            ],
            currentWords: '',
        }
    },
    methods:{
        showRandomImage(){
            const randomIndex = Math.floor(Math.random() * this.FFMW.length);
            this.currentWords = this.FFMW[randomIndex];
        }
    }
}

</script>