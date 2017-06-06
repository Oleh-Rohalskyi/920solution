<template>
  <div :style="mainStyle" class="block-component">
    <a class="logo" :class="'logo-'+blockName" href="#" :style="{width: '93px'}">
      <img :src="logoSrc" />
    </a>  
    <a class="rectangle-button" :class="'rectangle-button-'+blockName"  :style="{backgroundColor: colors.button[0], color: colors.button[1]}">
      GET A QUOTE
    </a>
    <slot></slot>
    <menu-component :block-name="blockName" :links="links" :colors="colors.menu" class="menu-position" :style="manuTopDistance" />
  </div>
</template>

<script>
import menuComponent from './menu/menu-component'

export default {
  name: 'block',
  props: ['colors', 'logoSrc', 'blockBg', 'blockName', 'links'],
  components: {
    menuComponent
  },
  computed: {
    mainStyle () {
      let bgConfig = this.$props.blockBg
      let style = bgConfig.gradient ? { backgroundImage: bgConfig.backgroundImage } : { background: bgConfig.background }
      return { ...style, height: '798px' }
    },
    manuTopDistance () {
      switch (this.blockName) {
        case 'portfolio':
          return { 'top': '27%' }
        case 'services':
          return { 'top': '28%' }
        case 'team':
          return { 'top': '28%' }
        case 'header':
          return { 'top': '36%' }
        case 'contact':
          return { 'top': '28.2%' }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
$blockHeightIndex: 100/798;
$blockWidthIndex: 100/1440;

.menu-position {
  position: absolute;
  top: 43%;
  left: $blockWidthIndex*75%;
}

.block-component {
  position: relative;
  width: 1440px;
  margin: 0 auto;
}

.logo {
  display: block;
  cursor: pointer;
  position: absolute;
  top: 27px;
  left: 47px;
  img {
    width: 100%
  }
  &-header {
    top: 40px;
  }
}

.rectangle-button {
  text-align: center;
  display: block;
  cursor: pointer;
  position: absolute;
  right: 30px;
  top: 25px;
  width: 124px;
  height: 34px;
  font-size: 14px;
  line-height: 35px;
  font-weight: 500;
  &-header {
    top: 30px;
  }
}
</style>
