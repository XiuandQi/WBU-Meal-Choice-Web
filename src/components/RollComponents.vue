<template>
    <div class="rollDiv">
        <button @click="ResetSelection" class="SFResetBtn">
          <img src="../assets/image/restartbtn.png" class="resetIcon">
        </button>
        <button @click="RandomRoll" class="rollBtn">抽<span>取</span></button>
    </div>
</template>

<script>
export default {
  name: 'RollComponents',
  props:['stores_data'],
  data(){
    return{
      selectedIndex: null
    }
  },
  methods: {
    RandomRoll() {
      this.selectedIndex = Math.floor(Math.random() * this.stores_data.length);
      console.log(this.selectedIndex);
      this.$emit("RandomRoll", this.selectedIndex);
    },

    ResetSelection() {
      this.selectedIndex = null;
      this.$emit("ResetSelection", this.selectedIndex);
    }
  }
}
</script>