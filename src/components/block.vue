<template>
  <div>
    <div :style="mainStyle" :class="['block-component', blockName+'-block']">
      <div class="navigation">
        <a class="logo" :class="'logo-'+blockName" href="#" :style="{width: '93px'}">
          <img :src="logoSrc" />
        </a>  
        <menu-component :block-name="blockName" :links="links" :colors="colors.menu" class="menu-position" :style="manuTopDistance" />
      </div>
        <slot></slot>
      <a class="rectangle-button" :class="'rectangle-button-'+blockName"  :style="{backgroundColor: colors.button[0], color: colors.button[1]}">
        GET A QUOTE
      </a>
    </div>
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
      return { ...style }
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

.navigation {
  display: flex;
  flex-direction: column;
  width: 283px;
}

.menu-position {
  margin: auto;
}


.block-component {
  display: flex;
  width: 100%;
  height: 100%;
  position: relative;
}

.logo {
  display: block;
  cursor: pointer;
  margin: 27px 0 0 47px;
  
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
