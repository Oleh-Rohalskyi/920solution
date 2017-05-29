<template>
    <li :class="{'selected': current }"><a :style="{ color: color }" :href="link">{{text}}</a></li>
</template>

<script>

export default {
  name: 'menu-link',
  props: ['current', 'color', 'text', 'link']
}
</script>

<style lang="scss" scoped>
    a {
      width: 100%;
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
