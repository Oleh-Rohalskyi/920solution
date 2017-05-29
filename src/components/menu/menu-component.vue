<template>
    <div class="menu" :class="'menu_' + blockName">
      <ul>
         <menu-link :value="''" :current="current.pcihology" :color="textColor(current.pcihology)" link="#" text="OUR PHILOSOPHY" />
         <menu-link :value="''" :current="current.portfolio" :color="textColor(current.portfolio)" link="#" text="PORTFOLIO" />
         <menu-link :value="''" :current="current.services" :color="textColor(current.services)" link="#" text="SERVICES" />
         <menu-link :value="''" :current="current.team" :color="textColor(current.team)" link="#" text="TEAM" />
         <menu-link :value="''" :current="current.contact" :color="textColor(current.contact)" link="#" text="CONTACT US" />
      </ul>
    </div>
  </div>
</template>

<script>
import menuLink from './menu-link'

export default {
  name: 'menu-component',
  props: ['colors', 'blockName'],
  components: {
    menuLink
  },
  data () {
    return {
      current: { services: true }
    }
  },
  methods: {
    textColor (current) {
      return current ? this.colors[1] : this.colors[0]
    }
  }
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
