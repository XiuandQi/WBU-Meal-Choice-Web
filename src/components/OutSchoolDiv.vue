<template>
    <div id="screenDiv" class="ScreenDiv right-go-on">
        <div>
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
          <div class="HiddenTips">
            <span>
              都校外了，不去吃大餐可惜了吧
            </span>
          </div>
        </div>
        <button @click="showHiddenTips" class="choiceBtn1">
          抽&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;取
        </button>
    </div>
</template>
<script>
export default {
  name: 'OutSchoolDiv',
  data(){
        return{

    }
  },
  methods:{
    showHiddenTips(){
      let hiddenTips = document.querySelector('.HiddenTips');
      hiddenTips.classList.toggle('HiddenTips_show');
    }
  }
}
</script>