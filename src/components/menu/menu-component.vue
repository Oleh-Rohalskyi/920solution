<template>
    <div class="menu"  :class="'menu_' + blockName">
      <ul>
         <menu-link v-for="(link,key) in links" :key="key" :colors="colors" :link="link.name" :text="link.linkText" />
      </ul>
    </div>
  </div>
</template>

<script>
import menuLink from './menu-link'

export default {
  name: 'menu-component',
  props: ['colors', 'blockName', 'links'],
  components: {
    menuLink
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
    .menu {
      width: 152px;
    }
    ul {
        font-size: 14px;
        line-height: 27px;
        list-style: none;
        margin: 0;
        padding: 0;
        text-align: left;
    }
</style>
