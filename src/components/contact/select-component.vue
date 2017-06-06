<template>
  <div class="contact">
        <label :for="'select'+forId">YOUR APPROXIMATE BUDGET</label>
        <select ref="select" :id="'select'+forId" class="select" @focus="open" @blur="close" type="text">
          <option v-model="model" @click="close" v-for="option in options" :value="option.value" v-text="option.text"></option>
        </select>
        <label ref="arrowBlock" :for="'select'+forId" class="arrow-block" @click="open">
            <div ref="triangle" class="triangle"></div>
        </label>
  </div>
</template>

<script>
export default {
  name: 'menu-component',
  props: ['options', 'model'],
  data () {
    return {
      forId: this._uid
    }
  },
  methods: {
    open () {
      this.$refs.select.size = this.options.length
      this.$refs.arrowBlock.style.height = this.$refs.select.offsetHeight - 2 + 'px'
      this.$refs.triangle.style.borderWidth = '0 5.5px 7 5.5px'
    },
    close () {
      this.$refs.triangle.style.borderWidth = '7px 5.5px 0 5.5px'
      this.$refs.arrowBlock.style.height = '50px'
      this.$refs.select.size = 1
    }
  }
}
</script>

<style lang="scss" scoped>
  .contact {
    height: 50px;
    margin-bottom: 40px;
  }
  label {
      display: block;
      font-family: "FuturaPTMedium";
      font-size: 14px;
      font-weight: 500;
      letter-spacing: 2px;
      color: #430f1b;
      margin-bottom: 4px;
      margin-top: 20px;
    }
  select:focus { 
    outline:0; 
    //border: 1px solid white;
  }

  .select {
      option {
        z-index: 7;
      }
      overflow-y: visible;
      z-index: 2;
      position: absolute;
      width: 420px;
      margin-bottom: 10px;
      //height: 50px;
      padding: 15px 0 14px 16px;
      background-color: #89233c;
      border: none;
      border-radius: 0;
      -webkit-appearance: none;
      -webkit-border-radius: 0px;
      font-family: 'helvetica';
      font-size: 18px;
      color: #ffffff;
      font-weight: 300;
    }
  .arrow-block {
    position: absolute;
    display: flex;
    right: 0;
    top: 108px;
    z-index: 3;
    background-color: white;
    height: 48px;
    width: 50px;
    background-color: #89233c;
  }
  
  select:focus+.arrow-block {
    // border-top: 1px solid white;
    // border-right: 1px solid white;
    // border-bottom: 1px solid white;
  }

  .triangle {
    align-self: center;
    margin: auto;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 7px 5.5px 0 5.5px;
    border-color: #e9e9e9 transparent transparent transparent;
    line-height: 0px;
  }
</style>
