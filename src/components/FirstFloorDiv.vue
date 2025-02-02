<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div class="firstMealDiv">
            <img :src="currentImage" class="firstMealImage">
        </div>
        <div class="choiceBtnDiv">
            <button @click="showRandomImage" class="choiceBtn">
                <img src="../assets/image/choice_btn.png" class="choiceBtnImg">
            </button>
        </div>
    </div>
</template>
<script>
export default {
    name: 'FirstFloorDiv',
    data(){
        return{
            images:[
                'src/assets/image/firstfloor/zizhu_first.png',
                'src/assets/image/firstfloor/tiantiantese.png',
                'src/assets/image/firstfloor/minzuchuangkou.png',
            ],
            currentImage: '',
        }
    },
    methods:{
        showRandomImage(){
            const randomIndex = Math.floor(Math.random() * this.images.length);
            this.currentImage = this.images[randomIndex];
        }
    }
}

</script>