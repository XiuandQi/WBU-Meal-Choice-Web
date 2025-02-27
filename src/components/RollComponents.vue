<template>
    <div class="rollDiv">
        <button @click="Reset" class="SFResetBtn">
          <img src="../assets/image/restartbtn.png" class="resetIcon">
        </button>
        <button @click="Roll" class="rollBtn">抽<span>取</span></button>
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
    Roll() {
      this.selectedIndex = Math.floor(Math.random() * this.stores_data.length);
      console.log(this.selectedIndex);
      this.$emit("Roll", this.selectedIndex);
    },

    Reset() {
      this.selectedIndex = null;
      this.$emit("Reset", this.selectedIndex);
    }
  }
}
</script>