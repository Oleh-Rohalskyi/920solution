<template>
    <li :class="{'selected': current }"><a v-smooth-scroll :href="'#'+link" :style="{ color: color }" >{{text}}</a></li>
</template>

<script>

export default {
  created () {
    this.color = this.current ? this.colors[1] : this.colors[0]
  },
  name: 'menu-link',
  props: ['colors', 'text', 'link'],
  data () {
    return {
      color: '',
      current: false
    }
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
    a {
      width: 100%;
      cursor: pointer;
    }
    li.selected {
        & a {
          margin-left: 18px;
        }
        &:before {
          content: '→'
        }
    }
</style>
